# Aetna

Aetna, a CVS Health company, offers health insurance, dental, vision, and other plans for individuals, families, employers, health care providers, and insurance agents and brokers. As a major U.S. health insurer, Aetna provides federally mandated FHIR R4 APIs for patient access, provider directory, and drug formulary data under CMS Interoperability and Patient Access Final Rule (CMS-9115-F). Provider connectivity is supported through the Availity portal for EDI transactions.

## APIs

### Aetna Patient Access FHIR API

FHIR R4 compliant Patient Access API providing members secure access to their health data including claims, clinical data, and coverage information. Required under CMS Interoperability and Patient Access Final Rule (CMS-9115-F). Supports SMART on FHIR authorization.

- [Documentation](https://www.aetna.com/individuals-families/member-rights-resources/member-data-access.html)

### Aetna Provider Directory FHIR API

FHIR R4 compliant Provider Directory API providing standardized access to in-network provider and facility information. Enables third-party applications to search for providers, verify network participation, and access provider details.

- [Documentation](https://www.aetna.com/health-care-professionals/working-with-aetna/provider-directory.html)

### Aetna Drug Formulary FHIR API

FHIR R4 compliant Drug Formulary API providing standardized access to plan formulary data including covered drugs, tiers, cost-sharing requirements, and prior authorization requirements. Implements the DaVinci PDEX Formulary Implementation Guide.

- [Documentation](https://www.aetna.com/individuals-families/member-rights-resources/member-data-access.html)

### Aetna Provider EDI API

Electronic Data Interchange connectivity for healthcare providers enabling electronic submission of claims, eligibility verification, claim status inquiries, and remittance advice. Accessible through the Availity provider portal supporting EDI 837, 270/271, 276/277, and 835 HIPAA transactions.

- [Documentation](https://www.aetna.com/health-care-professionals/claims-payment/claims-submission.html)
- [Portal](https://www.availity.com)

## Properties

- [Website](https://www.aetna.com)
- [Provider Portal](https://www.aetna.com/health-care-professionals.html)
- [Member Login](https://member.aetna.com)
- [Support](https://www.aetna.com/individuals-families/contact-aetna.html)
- [Privacy Policy](https://www.aetna.com/legal-notices/privacy.html)
- [Terms of Service](https://www.aetna.com/legal-notices/terms-of-use.html)

## Features

- **FHIR R4 Compliance** — All patient-facing APIs implement HL7 FHIR Release 4 standard for interoperability.
- **SMART on FHIR Authorization** — Secure OAuth 2.0 authorization framework for patient-authorized third-party app access.
- **CMS Interoperability Compliance** — Full compliance with CMS-9115-F Interoperability and Patient Access Final Rule.
- **EDI Transaction Support** — Complete HIPAA-compliant EDI transaction set for provider administrative workflows.
- **Payer-to-Payer Data Exchange** — Supports member-directed payer-to-payer data exchange for continuity of care.
- **DaVinci Implementation Guides** — Implements HL7 DaVinci Project PDEX, PDex Drug Formulary, and Plan Net guides.

## Use Cases

- **Member Health Record Access** — Members use SMART on FHIR apps to access their complete health records across providers.
- **Provider Network Verification** — Developers build directory search tools to help patients find in-network providers.
- **Drug Cost Comparison** — Applications use formulary API to compare medication costs across Aetna plans.
- **Electronic Claims Submission** — Healthcare providers submit claims electronically via EDI 837 transactions through Availity.
- **Eligibility Verification** — Providers verify member eligibility and benefits in real time using 270/271 EDI transactions.
- **Remittance Processing** — Providers receive and process electronic remittance advice via EDI 835 transactions.

## Integrations

- **CVS Caremark** — Integrated pharmacy benefit management for prescription drug coverage and mail-order pharmacy.
- **Availity** — Primary provider portal for EDI transactions, eligibility, claims, and authorization requests.
- **Epic Payer Platform** — EHR integration enabling clinical workflows including prior authorization and care management.
- **Apple Health** — FHIR-based integration enabling Aetna members to view health data in Apple Health app.
- **CommonWell Health Alliance** — Interoperability network participation for cross-organization health data exchange.
- **CMS Blue Button 2.0** — Alignment with CMS Blue Button 2.0 FHIR API patterns for Medicare data access.

## Artifacts

- [Vocabulary](vocabulary/aetna-vocabulary.yaml)
