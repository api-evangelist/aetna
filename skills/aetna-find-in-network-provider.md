---
name: Find an in-network Aetna provider
description: >-
  Search Aetna's Da Vinci PDex Plan Net provider directory for practitioners, the organizations and
  locations they practise at, and the insurance plans whose networks they participate in.
api: openapi/aetna-provider-directory-api-openapi.yml
operations:
  - get_v1_providerdirectory_Practitioner
  - get_v1_providerdirectory_PractitionerRole
  - get_v1_providerdirectory_Organization
  - get_v1_providerdirectory_Location
  - get_v1_providerdirectory_InsurancePlan
generated: '2026-08-30'
method: generated
source: openapi/aetna-provider-directory-api-openapi.yml, https://apif1.aetna.com/fhir/v1/providerdirectory/metadata
---

# Find an in-network Aetna provider

Base URL: `https://apif1.aetna.com/fhir`. Live CapabilityStatement:
`https://apif1.aetna.com/fhir/v1/providerdirectory/metadata` (anonymous GET, HTTP 200 — read it first,
it is the authoritative parameter list).

**Aetna's provider directory requires OAuth.** Several peer payers expose their directory
anonymously because it contains no member data; Aetna does not. Its specs declare oauth2 on every
directory operation, including a client-credentials scheme with `Public` and `NonPII` scopes. Get a
token before you start.

## Two directory surfaces, and they are not the same

- `/v1/providerdirectory/...` — the interactive directory. Practitioner, PractitionerRole,
  Organization, OrganizationAffiliation, InsurancePlan, Location.
- `/v1/providerdirectorydata/...` — the same resources plus HealthcareService, and the surface that
  carries Bulk FHIR `$export` / `$exportstatus/{id}`. This is the family that declares 401/403/405/429
  and the optional `x-clientrefid` correlation header.

Prefer `providerdirectorydata` for anything bulk or high-volume; prefer `providerdirectory` for
one-off lookups.

## 1. Find the clinician

`get_v1_providerdirectory_Practitioner` — `GET /v1/providerdirectory/Practitioner`.

Useful declared parameters: `name`, `name:contains`, `identifier` (NPI), `_id`,
`address-city:exact`, `address-state:exact`, `address-postalcode:exact`.

`get_v1_providerdirectory_Practitioner_id` reads one by logical id.

## 2. Resolve the role — this is the step that answers "in network?"

`get_v1_providerdirectory_PractitionerRole` — `GET /v1/providerdirectory/PractitionerRole`.

PractitionerRole is the join. It binds a practitioner to the organization they practise for, the
locations they work at, the specialty they practise, and — critically — the `network` they
participate in. A practitioner record alone tells you nothing about network participation.

Search by `practitioner`, `organization`, `location`, `specialty`, `network`.

## 3. Fill in the surroundings

- `get_v1_providerdirectory_Organization` / `..._Organization_id` — the group or facility.
- `get_v1_providerdirectory_Location` / `..._Location_id` — the address, searchable by
  `address-city:exact`, `address-state:exact`, `address-postalcode:exact`.
- `get_v1_providerdirectory_InsurancePlan` — the plans whose networks these roles belong to.
- `OrganizationAffiliation` — how organizations relate to one another.

## 4. Going bulk

For a whole network rather than a lookup, use `$export` on `/v1/providerdirectorydata` and poll
`$exportstatus/{id}`. Aetna added this on 2023-09-29 with `_since` and `_type` parameters; `_type`
accepts the seven Plan Net profiles (HealthcareService, InsurancePlan, Location, Organization,
OrganizationAffiliation, Practitioner, PractitionerRole). Those two operations are catalogued by
Aetna but their spec documents were not retrievable when this skill was written, so confirm the exact
request shape against the CapabilityStatement before relying on it.

## Rules that will bite you

- **Paginate by `Bundle.link` `next`.** Parts of this directory use a numeric `page` parameter
  (Aetna's example: `first`=page=1, `next`=page=11) rather than `_page_token`. Follow the link, don't
  guess the idiom.
- **`_count` caps the page size**, it does not cap the result set.
- **Unknown parameters return 400.**
- **429 is policed by source IP**, with a FHIR `OperationOutcome` body and no `Retry-After`.
- **Watch for 203.** Two directory read operations declare `203 Non-Authoritative Information`. Code
  that treats only `200` as success will mishandle it.
- **The Da Vinci IG moved to 1.2.0 on 2026-06-23**, adding search parameters to PractitionerRole,
  InsurancePlan and HealthcareService. Aetna states it is non-breaking, but the CapabilityStatement
  saved in `fhir/` predates it — re-read `/metadata` rather than trusting the archived copy.
- **Directory data is only as fresh as Aetna's feed.** There is no `Last-Modified`, no `ETag` and no
  cache guidance in the contract, so you cannot make a conditional request.
