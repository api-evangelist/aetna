---
name: Retrieve an Aetna member's claims and coverage
description: >-
  Authorize as an Aetna member under SMART App Launch, then read that member's coverage and pull their
  Explanation of Benefit history from the CARIN Blue Button Patient Access API.
api: openapi/aetna-patient-access-api-openapi.yml
operations:
  - get_v2_patientaccess_Patient
  - get_v2_patientaccess_Coverage
  - get_v2_patientaccess_ExplanationOfBenefit
  - get_v2_patientaccess_ExplanationOfBenefit_id
generated: '2026-08-30'
method: generated
source: openapi/aetna-patient-access-api-openapi.yml, conventions/aetna-conventions.yml, errors/aetna-problem-types.yml
---

# Retrieve an Aetna member's claims and coverage

Base URL: `https://apif1.aetna.com/fhir` (sandbox: `https://vteapif1.aetna.com/fhirdemo`).

## 1. Get authorized

You cannot call anything anonymously. Run the SMART App Launch authorization-code flow:

- authorize: `https://apif1.aetna.com/fhir/prod/v1/fhirserver_auth/oauth2/authorize`
- token: `https://apif1.aetna.com/fhir/prod/v1/fhirserver_auth/oauth2/token`
- client authentication: `client_secret_basic` (send the Client ID/Secret as a Basic auth header)
- PKCE: required for public clients, `code_challenge_method=S256`
- scopes: `launch/patient patient/*.read` at minimum; add `openid fhirUser profile` for identity
- the member signs in during the authorize step — the token is bound to their patient context

Aetna's own token-generation guide passes `aud=https://apif1.aetna.com/fhir` on the authorize request.
Its guide and its CapabilityStatements name `/fhir/v1/fhirserver_auth/...` while the live
`smart-configuration` names `/fhir/prod/v1/fhirserver_auth/...`. Read
`https://apif1.aetna.com/fhir/.well-known/smart-configuration` at runtime and use what it returns.

Before any of this works the application must be **subscribed** in the Aetna Developer Portal to the
product that contains the API. An unsubscribed call returns 401, not 403.

## 2. Confirm who the token is for

`get_v2_patientaccess_Patient` — `GET /v2/patientaccess/Patient` returns the patient in context.
`get_v2_patientaccess_Patient_id` reads one by logical id. Send `Accept: application/json` (Aetna
declares `application/json`, not `application/fhir+json`).

## 3. Read coverage

`get_v2_patientaccess_Coverage` — `GET /v2/patientaccess/Coverage?patient={id}`. This tells you the
plan, the payor and the benefit period before you interpret any claim.

## 4. Pull the Explanation of Benefit history

`get_v2_patientaccess_ExplanationOfBenefit` — `GET /v2/patientaccess/ExplanationOfBenefit`.

Parameters Aetna declares on this operation:

- `patient` — the patient identifier
- `_id` — the logical identifier of one EOB
- `service-date` — prefixed date, e.g. `service-date=ge2019-01-01` (`ge` and `le` are supported)
- `_profile` — select a CARIN Blue Button profile. Aetna documents these StructureDefinition URLs:
  `C4BB-ExplanationOfBenefit` (base), `-Pharmacy`, `-Inpatient-Institutional`,
  `-Outpatient-Institutional`, `-Professional-NonClinician`
- `_count`, `_page_token`, `_revinclude`

Use `get_v2_patientaccess_ExplanationOfBenefit_id` to read one EOB by id.

## 5. Page correctly

The response is a FHIR `Bundle` of type `searchset`. Follow `Bundle.link` where `relation == "next"`
verbatim and pass the server-issued `_page_token` back — do not construct page URLs yourself, and do
not assume a numeric page parameter on this API (that idiom belongs to parts of the provider directory).

## Rules that will bite you

- **Do not send parameters that are not declared.** Aetna returns 400 for an unknown parameter, not
  just for a missing required one.
- **Errors are FHIR `OperationOutcome`, not RFC 9457 problem+json.** Read `issue[].code` and
  `issue[].details.coding[].code`; quote `OperationOutcome.id` to support.
- **429 means source-IP throttling.** Aetna publishes no numeric limit, no `Retry-After` and no
  `RateLimit-*` headers, so back off exponentially with jitter on your own schedule.
- **This surface is read-only.** Every operation is a GET. There is nothing to make idempotent and
  nothing to reverse.
- **Eligibility is not universal.** Patient Access reaches Medicare and Medicaid members plus fully
  insured Commercial members in the states Aetna has enabled (California from 2023-12-15, Tennessee
  from 2025-05-15). A 404 can mean "this member is not in scope", not "this member does not exist".
- **Check the implementation-guide version before mapping fields.** Aetna runs US Core 3.1.1, 5.0.1 and
  6.1.0 on different operations; `https://developerportal.aetna.com/assets/Data/Fhir.json` names the
  version per operation.

Support: `InteroperabilityDeveloperSupport@aetna.com`.
