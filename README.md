# Aetna

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Aetna, a CVS Health company, is one of the largest U.S. health insurers, offering medical, dental, vision, pharmacy and Medicare/Medicaid plans to individuals, families, employers, health care providers and brokers. Its public API surface is entirely regulatory: Aetna operates an Interoperability API Developer Portal at developerportal.aetna.com that publishes HL7 FHIR R4 interfaces mandated by the CMS Interoperability and Patient Access Final Rule (CMS-9115-F) and the Advancing Interoperability and Improving Prior Authorization Final Rule (CMS-0057-F) - Patient Access, Payer to Payer, Provider Directory, Provider Access, Prior Authorization (Da Vinci CRD, PAS and CDex) and Realtime Pharmacy Benefit Check. Aetna publishes a machine-readable catalog of 139 operations and serves a Swagger 2.0 document for each one, plus live FHIR CapabilityStatements and SMART App Launch discovery documents on its production and sandbox FHIR gateways. Everything is read-only, everything requires OAuth 2.0 under SMART App Launch, and everything is free - there is no pricing, no plan and no metered product. Provider EDI connectivity is handled separately through the Availity portal.

**Areas:** Health Insurance · Healthcare · FHIR · Patient Access · Provider Directory · Drug Formulary · Prior Authorization · CMS Interoperability · SMART on FHIR · CARIN Blue Button · Da Vinci · Payers

## Aetna on APIs.io

Everything profiled for Aetna is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/aetna/](https://apis.io/providers/aetna/)** — or go straight to one of the APIs or properties below.

### APIs (15)

- [Aetna Prior Authorization FHIR API](https://apis.io/apis/aetna/aetna-prior-authorization-fhir-api/) — Da Vinci prior-authorization surface built for CMS-0057-F: Coverage Requirements Discovery (STU 2.1) at /coveragerequirementsdiscovery/v1/cds-services/{id}…
- [Aetna Provider Access FHIR API](https://apis.io/apis/aetna/aetna-provider-access-fhir-api/) — Launched in Production on 2026-03-27 under the public-provider-group-fhir product, the Provider Access API lets provider organizations and EHR vendors…
- [Aetna Realtime Pharmacy Benefit Check API](https://apis.io/apis/aetna/aetna-realtime-pharmacy-benefit-check-api/) — Consumer Real-Time Pharmacy Benefit Check 1.0.0, launched 2024-12-05, letting members and EHR systems retrieve prescription drug cost and coverage…
- [Aetna Provider EDI Connectivity](https://apis.io/apis/aetna/aetna-provider-edi-api/) — HIPAA X12 electronic data interchange for health care professionals - EDI 837 claims, 270/271 eligibility and benefits, 276/277 claim status and 835…
- [Aetna Endpoint API](https://apis.io/apis/aetna/aetna-endpoint-api/) — The Endpoint API from Aetna — 2 operation(s) for endpoint.
- [Aetna Location API](https://apis.io/apis/aetna/aetna-location-api/) — The Location API from Aetna — 2 operation(s) for location.
- [Aetna Organization API](https://apis.io/apis/aetna/aetna-organization-api/) — The Organization API from Aetna — 2 operation(s) for organization.
- [Aetna Organization Affiliation API](https://apis.io/apis/aetna/aetna-organizationaffiliation-api/) — The OrganizationAffiliation API from Aetna — 1 operation(s) for organizationaffiliation.
- [Aetna Practitioner API](https://apis.io/apis/aetna/aetna-practitioner-api/) — The Practitioner API from Aetna — 2 operation(s) for practitioner.
- [Aetna Providerdirectorydata API](https://apis.io/apis/aetna/aetna-providerdirectorydata-api/) — The Providerdirectorydata API from Aetna — 11 operation(s) for providerdirectorydata.
- [Aetna Patient Access API](https://apis.io/apis/aetna/aetna-patient-access-api/) — The Patient Access API from Aetna — 83 operation(s) for patient access.
- [Aetna Provider Directory API](https://apis.io/apis/aetna/aetna-provider-directory-api/) — The Provider Directory API from Aetna — 9 operation(s) for provider directory.
- [Aetna Healthcare Service API](https://apis.io/apis/aetna/aetna-healthcare-service-api/) — The Healthcare Service API from Aetna — 2 operation(s) for healthcare service.
- [Aetna Insurance Plan API](https://apis.io/apis/aetna/aetna-insurance-plan-api/) — The Insurance Plan API from Aetna — 1 operation(s) for insurance plan.
- [Aetna Practitioner Role API](https://apis.io/apis/aetna/aetna-practitioner-role-api/) — The Practitioner Role API from Aetna — 1 operation(s) for practitioner role.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### GraphQL (1)

GraphQL schemas.

- [Moved to /providers/aetna/](https://apis.io/graphqls/aetna/aetna-graphql/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [aetna](https://apis.io/servers/aetna/aetna/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Aetna Agentic Access](https://apis.io/agentic-access/aetna/aetna-agentic-access/)

#### JSON Schema (25)

The data models the API reads and writes.

- [Aetna FHIR R4 AllergyIntolerance](https://apis.io/schemas/aetna/aetna-allergyintolerance/)
- [Aetna FHIR R4 Bundle](https://apis.io/schemas/aetna/aetna-bundle/)
- [Aetna FHIR R4 CarePlan](https://apis.io/schemas/aetna/aetna-careplan/)
- [Aetna FHIR R4 CareTeam](https://apis.io/schemas/aetna/aetna-careteam/)
- [Aetna FHIR R4 Condition](https://apis.io/schemas/aetna/aetna-condition/)
- [Aetna FHIR R4 Device](https://apis.io/schemas/aetna/aetna-device/)
- [Aetna FHIR R4 DiagnosticReport](https://apis.io/schemas/aetna/aetna-diagnosticreport/)
- [Aetna FHIR R4 DocumentReference](https://apis.io/schemas/aetna/aetna-documentreference/)
- [Aetna FHIR R4 Encounter](https://apis.io/schemas/aetna/aetna-encounter/)
- [Aetna FHIR R4 ExplanationOfBenefit](https://apis.io/schemas/aetna/aetna-explanationofbenefit/)
- [Aetna FHIR R4 Goal](https://apis.io/schemas/aetna/aetna-goal/)
- [Aetna FHIR R4 HealthcareService](https://apis.io/schemas/aetna/aetna-healthcareservice/)
- [Aetna FHIR R4 Immunization](https://apis.io/schemas/aetna/aetna-immunization/)
- [Aetna FHIR R4 InsurancePlan](https://apis.io/schemas/aetna/aetna-insuranceplan/)
- [Aetna FHIR R4 Location](https://apis.io/schemas/aetna/aetna-location/)
- [Aetna FHIR R4 MedicationKnowledge](https://apis.io/schemas/aetna/aetna-medicationknowledge/)
- [Aetna FHIR R4 MedicationRequest](https://apis.io/schemas/aetna/aetna-medicationrequest/)
- [Aetna FHIR R4 Observation](https://apis.io/schemas/aetna/aetna-observation/)
- [Aetna FHIR R4 OperationOutcome](https://apis.io/schemas/aetna/aetna-operationoutcome/)
- [Aetna FHIR R4 Organization](https://apis.io/schemas/aetna/aetna-organization/)
- [Aetna FHIR R4 OrganizationAffiliation](https://apis.io/schemas/aetna/aetna-organizationaffiliation/)
- [Aetna FHIR R4 Patient](https://apis.io/schemas/aetna/aetna-patient/)
- [Aetna FHIR R4 Practitioner](https://apis.io/schemas/aetna/aetna-practitioner/)
- [Aetna FHIR R4 PractitionerRole](https://apis.io/schemas/aetna/aetna-practitionerrole/)
- [Aetna FHIR R4 Procedure](https://apis.io/schemas/aetna/aetna-procedure/)

#### Vocabulary (1)

The provider's domain terms, defined.

- [Aetna Vocabulary](https://apis.io/vocabularies/aetna/aetna-vocabulary/)

#### Examples (70)

Example requests and responses.

- [Aetna V1 Providerdirectory Insuranceplan 200 Example](https://apis.io/examples/aetna/aetna-v1-providerdirectory-insuranceplan-200-example/)
- [Aetna V1 Providerdirectory Insuranceplan 400 Example](https://apis.io/examples/aetna/aetna-v1-providerdirectory-insuranceplan-400-example/)
- [Aetna V1 Providerdirectory Insuranceplan 500 Example](https://apis.io/examples/aetna/aetna-v1-providerdirectory-insuranceplan-500-example/)
- [Aetna V1 Providerdirectory Location 200 Example](https://apis.io/examples/aetna/aetna-v1-providerdirectory-location-200-example/)
- [Aetna V1 Providerdirectory Location 400 Example](https://apis.io/examples/aetna/aetna-v1-providerdirectory-location-400-example/)
- [Aetna V1 Providerdirectory Location 500 Example](https://apis.io/examples/aetna/aetna-v1-providerdirectory-location-500-example/)
- [Aetna V1 Providerdirectory Location Id 200 Example](https://apis.io/examples/aetna/aetna-v1-providerdirectory-location-id-200-example/)
- [Aetna V1 Providerdirectory Location Id 400 Example](https://apis.io/examples/aetna/aetna-v1-providerdirectory-location-id-400-example/)
- [Aetna V1 Providerdirectory Location Id 404 Example](https://apis.io/examples/aetna/aetna-v1-providerdirectory-location-id-404-example/)
- [Aetna V1 Providerdirectory Location Id 500 Example](https://apis.io/examples/aetna/aetna-v1-providerdirectory-location-id-500-example/)
- [Aetna V1 Providerdirectory Organization 200 Example](https://apis.io/examples/aetna/aetna-v1-providerdirectory-organization-200-example/)
- [Aetna V1 Providerdirectory Organization 400 Example](https://apis.io/examples/aetna/aetna-v1-providerdirectory-organization-400-example/)
- [Aetna V1 Providerdirectory Organization 500 Example](https://apis.io/examples/aetna/aetna-v1-providerdirectory-organization-500-example/)
- [Aetna V1 Providerdirectory Organization Id 200 Example](https://apis.io/examples/aetna/aetna-v1-providerdirectory-organization-id-200-example/)
- [Aetna V1 Providerdirectory Organization Id 203 Example](https://apis.io/examples/aetna/aetna-v1-providerdirectory-organization-id-203-example/)
- [Aetna V1 Providerdirectory Organization Id 400 Example](https://apis.io/examples/aetna/aetna-v1-providerdirectory-organization-id-400-example/)
- [Aetna V1 Providerdirectory Organization Id 404 Example](https://apis.io/examples/aetna/aetna-v1-providerdirectory-organization-id-404-example/)
- [Aetna V1 Providerdirectory Organization Id 500 Example](https://apis.io/examples/aetna/aetna-v1-providerdirectory-organization-id-500-example/)
- [Aetna V1 Providerdirectory Organizationaffiliation 200 Example](https://apis.io/examples/aetna/aetna-v1-providerdirectory-organizationaffiliation-200-example/)
- [Aetna V1 Providerdirectory Organizationaffiliation 400 Example](https://apis.io/examples/aetna/aetna-v1-providerdirectory-organizationaffiliation-400-example/)
- [Aetna V1 Providerdirectory Organizationaffiliation 500 Example](https://apis.io/examples/aetna/aetna-v1-providerdirectory-organizationaffiliation-500-example/)
- [Aetna V1 Providerdirectory Practitioner 200 Example](https://apis.io/examples/aetna/aetna-v1-providerdirectory-practitioner-200-example/)
- [Aetna V1 Providerdirectory Practitioner 400 Example](https://apis.io/examples/aetna/aetna-v1-providerdirectory-practitioner-400-example/)
- [Aetna V1 Providerdirectory Practitioner 500 Example](https://apis.io/examples/aetna/aetna-v1-providerdirectory-practitioner-500-example/)
- [Aetna V1 Providerdirectory Practitioner Id 200 Example](https://apis.io/examples/aetna/aetna-v1-providerdirectory-practitioner-id-200-example/)
- …and 45 more published on APIs.io

#### Overlays (3)

OpenAPI overlays, including conversational phrasing for each operation.

- [Aetna Patient Access Api Overlay](https://apis.io/overlays/aetna/aetna-patient-access-api-overlay/)
- [Aetna Patient Access Api Sandbox Overlay](https://apis.io/overlays/aetna/aetna-patient-access-api-sandbox-overlay/)
- [Aetna Provider Directory Api Overlay](https://apis.io/overlays/aetna/aetna-provider-directory-api-overlay/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Aetna Authentication](https://apis.io/security/aetna/aetna-authentication/)
- [Aetna Domain Security](https://apis.io/security/aetna/aetna-domain-security/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Aetna Scopes](https://apis.io/scopes/aetna/aetna-scopes/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Aetna Plans Pricing](https://apis.io/plans/aetna/aetna-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Aetna Rate Limits](https://apis.io/rate-limits/aetna/aetna-rate-limits/)

#### FinOps (1)

What the API costs to run, by operation.

- [Aetna Finops](https://apis.io/finops/aetna/aetna-finops/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.aetna.com)
- [Documentation](https://developerportal.aetna.com/)
- [Getting started](https://developerportal.aetna.com/gettingstarted/1000)
- [API reference](https://developerportal.aetna.com/assets/Data/Fhir.json)
- [Sign up](https://developerportal.aetna.com/)
- [Support](https://www.aetna.com/individuals-families/contact-aetna.html)
- [Changelog](https://developerportal.aetna.com/managedcontent/pdfs/Previous_Releases.pdf)
- [Blog](https://www.aetna.com/news/)
- [Terms of service](https://developerportal.aetna.com/termsofuse)
- [Privacy policy](https://www.aetna.com/legal-notices/privacy.html)
- [GitHub](https://github.com/aetnahealth)

## API Evangelist rating

**Kin Score 45.1** — developing · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 71.4 |
| Contract quality | 52.7 |
| Contract governance | 31.8 |
| Operational transparency | 31.6 |
| Developer ergonomics | 35.1 |
| Access clarity | 25.0 |

**Agent readiness 41.3** — agent-native

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | na |
| MCP Server | — |
| Auth Clarity | negotiable (partial credit) |
| Idempotency | na |
| Error Semantics | verified |
| OpenAPI Examples | verified |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | — |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | na |
| Delegated Identity | documented (partial credit) |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | na |
| Operation Distinctiveness | — |

**Regulatory alignment 44.5** — Health

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/aetna/](https://apis.io/providers/aetna/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Aetna: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/aetna/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
