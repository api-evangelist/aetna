---
name: Check Aetna drug coverage and formulary tier
description: >-
  Use the Da Vinci US Drug Formulary resources on Aetna's Patient Access API to find whether a drug is
  covered, at what tier, and with what restrictions.
api: openapi/aetna-patient-access-api-openapi.yml
operations:
  - get_v2_patientaccess_MedicationKnowledge
  - get_v2_patientaccess_MedicationKnowledge_id
  - get_v2_patientaccess_MedicationRequest
  - get_v2_patientaccess_Medication_id
generated: '2026-08-30'
method: generated
source: openapi/aetna-patient-access-api-openapi.yml, changelog/aetna-changelog.yml, conformance/aetna-conformance.yml
---

# Check Aetna drug coverage and formulary tier

Base URL: `https://apif1.aetna.com/fhir`. Requires a SMART App Launch token — see
`skills/aetna-retrieve-member-claims.md` for the authorization flow.

Aetna implements **Da Vinci PDex US Drug Formulary 2.0.0 STU 2**.

## 1. Look up the drug

`get_v2_patientaccess_MedicationKnowledge` — `GET /v2/patientaccess/MedicationKnowledge`. This is the
formulary resource: it carries the drug, its tier, cost-sharing and any restriction such as prior
authorization or step therapy. It is the single richest search surface Aetna publishes, declaring 11
search parameters in its CapabilityStatement.

`get_v2_patientaccess_MedicationKnowledge_id` reads one entry by logical id.

## 2. Cross-check what the member is actually taking

`get_v2_patientaccess_MedicationRequest` — `GET /v2/patientaccess/MedicationRequest?patient={id}` —
returns the member's prescriptions. `get_v2_patientaccess_Medication_id` resolves a referenced
Medication resource.

## 3. Know what changed under you

The formulary surface was restructured on 2024-04-19 when Aetna moved to US Drug Formulary 2.0.0 STU 2:

- the **List API was decommissioned** from the Patient Access products;
- MedicationKnowledge was upgraded to STU 2 with major changes to profiles, resources and search
  parameters;
- new formulary **InsurancePlan**, **Basic** and **Location** resources were added to the Patient
  Access product;
- FHIR server endpoint URLs did not change, and no subscription change was required.

Those three new formulary resources are catalogued by Aetna but their spec documents could not be
retrieved when this skill was written (HTTP 403), so their exact parameters are not grounded here.
Read `https://apif1.aetna.com/fhir/v2/patientaccess/metadata` — it lists `InsurancePlan` with 15
search parameters and `Basic` with 13 — before calling them.

## Rules that will bite you

- **The formulary is plan-specific.** Read the member's `Coverage` first; a tier means nothing without
  knowing which plan it belongs to.
- **Errors are FHIR `OperationOutcome`.** A 404 on a drug lookup means "no match", carried as
  `issue[].details.coding[].code = MSG_NO_MATCH`.
- **Unknown query parameters return 400.**
- **Read-only.** There is no way to submit a coverage-determination request through this API; prior
  authorization lives on a different surface entirely (`/priorauthorizationsupport/v1/Claim/$submit`,
  Da Vinci PAS STU 2.1), which this repo does not have a contract for.
- **Pharmacy prior auth is explicitly out of scope** for Aetna's Coverage Requirements Discovery
  service, per its own 2025-04-04 release note.
