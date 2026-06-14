# Aetna GraphQL Schema

## Overview

Aetna, a CVS Health company, is a major U.S. health insurer offering health insurance, dental, vision, pharmacy, and wellness plans for individuals, families, employers, healthcare providers, and brokers. This conceptual GraphQL schema is derived from Aetna's publicly documented capabilities including the federally mandated FHIR R4 APIs (CMS-9115-F), the Availity EDI provider portal, the CVS Caremark pharmacy benefit management system, and the broader Aetna developer portal at https://developer.aetna.com/.

The schema represents the primary business domains: member identity and enrollment, plan and coverage details, provider directory, claims and explanation of benefits, prior authorization, pharmacy and formulary, wellness and behavioral health, and API access management.

## Schema Source

Conceptual — derived from:

- https://developer.aetna.com/
- https://www.aetna.com/individuals-families/member-rights-resources/member-data-access.html
- https://www.aetna.com/health-care-professionals/working-with-aetna/provider-directory.html
- HL7 FHIR R4 ExplanationOfBenefit, Coverage, Patient, MedicationKnowledge resources
- HL7 DaVinci PDex, PDex Drug Formulary, and Plan Net Implementation Guides
- CMS Interoperability and Patient Access Final Rule (CMS-9115-F)

## Types

### Member and Identity

- `Member` — core member record with demographics, enrollment status, and plan linkage
- `MemberId` — member identifier including plan ID, group number, and subscriber ID
- `MemberProfile` — extended member profile including contact preferences and communication settings
- `MemberServices` — member services contact information and support options

### Plan and Coverage

- `InsurancePlan` — base insurance plan record with type, effective dates, and network
- `CommercialPlan` — commercial (employer-sponsored or individual market) plan details
- `MedicarePlan` — Medicare Advantage plan details including Part C and Part D coverage
- `MedicaidPlan` — Medicaid managed care plan details
- `PlanDetails` — plan-level details including benefit year, market, and metal tier
- `Coverage` — member-specific coverage record linking a member to a plan
- `Deductible` — deductible amounts and accumulator balances (individual and family)
- `OutOfPocket` — out-of-pocket maximum amounts and accumulator balances
- `Copay` — copayment amounts by service type
- `Coinsurance` — coinsurance percentages by service type
- `PlanMaximum` — plan benefit maximums by category
- `WellnessBenefit` — wellness incentive program benefits and eligibility
- `NetworkType` — network type classification (HMO, PPO, EPO, POS, HDHP)

### Provider Directory

- `Provider` — base provider record with NPI, name, specialty, and contact
- `ProviderDirectory` — searchable provider directory with network participation status
- `PCP` — primary care physician record with panel status and accepting-new-patients flag
- `OB` — obstetrics provider record
- `Specialist` — specialist provider record with specialty taxonomy codes
- `Hospital` — hospital or health system facility record
- `LabNetwork` — clinical laboratory network participation record
- `ImageCenter` — radiology and imaging center record
- `InNetworkProvider` — in-network provider participation details for a specific plan
- `OutOfNetworkProvider` — out-of-network provider cost-sharing details

### Behavioral and Mental Health

- `MentalHealth` — mental health benefit details and provider listings
- `BehavioralHealth` — behavioral health benefit details including inpatient and outpatient
- `SubstanceUse` — substance use disorder treatment benefit details
- `EAP` — employee assistance program benefit details and access information
- `UrbanHealth` — urban and community health program details

### Pharmacy and Formulary

- `Pharmacy` — pharmacy record with network participation and location
- `PharmacyNetwork` — pharmacy network details for a specific plan
- `MailOrder` — CVS Caremark mail-order pharmacy details
- `MinuteClinic` — CVS MinuteClinic location and service details
- `CVSLocation` — CVS retail location record combining pharmacy and MinuteClinic data
- `Formulary` — drug formulary for a specific plan and benefit year
- `DrugTier` — formulary drug tier with cost-sharing rules
- `DrugBenefit` — member-specific drug benefit details
- `SpecialtyDrug` — specialty medication record with prior authorization requirements
- `MedNecessity` — medical necessity criteria for a drug or service

### Telehealth

- `Teladoc` — Teladoc Health virtual care benefit details
- `Telehealth` — general telehealth benefit record covering multiple virtual care programs

### Claims and EOB

- `Claim` — healthcare claim record with service dates, provider, and amounts
- `ClaimLine` — individual service line within a claim
- `ClaimStatus` — real-time claim status information
- `ClaimPayment` — claim payment details including check or EFT information
- `ExplanationOfBenefits` — explanation of benefits document for a processed claim
- `EOBLine` — individual service line within an EOB with cost-sharing breakdown
- `Denial` — claim denial record with denial reason codes
- `Appeal` — claim appeal record with appeal status and decision

### Prior Authorization

- `PreAuthorization` — prior authorization record with status and approved services
- `AuthRequest` — authorization request with clinical details and requested services
- `ClinicalReview` — clinical review record for a prior authorization or appeal

### Wellness and Health Management

- `Wellness` — wellness program enrollment and activity tracking
- `HealthCoach` — health coaching program details and coach assignment
- `HRA` — health risk assessment record with completion status and results

### API Access

- `APIKey` — API key credential for developer portal access
- `Token` — OAuth 2.0 / SMART on FHIR access token record
- `Webhook` — webhook subscription for event-driven notifications

## Queries

- `member(memberId: ID!)` — fetch a single member record
- `memberCoverage(memberId: ID!, planYear: Int)` — fetch coverage details for a member
- `searchProviders(specialty: String, location: String, planId: ID, radius: Int)` — search provider directory
- `provider(npi: String!)` — fetch a single provider by NPI
- `formulary(planId: ID!, benefitYear: Int)` — fetch formulary for a plan
- `drug(rxcui: String!)` — fetch drug formulary details by RxCUI
- `claims(memberId: ID!, dateFrom: String, dateTo: String)` — list claims for a member
- `claim(claimId: ID!)` — fetch a single claim
- `eob(claimId: ID!)` — fetch explanation of benefits for a claim
- `preAuthorization(authId: ID!)` — fetch a prior authorization record
- `cvsLocation(zip: String!, radius: Int)` — find CVS and MinuteClinic locations

## Mutations

- `submitAuthRequest(input: AuthRequestInput!)` — submit a prior authorization request
- `createWebhook(input: WebhookInput!)` — register a webhook subscription
- `deleteWebhook(webhookId: ID!)` — remove a webhook subscription
- `updateMemberProfile(memberId: ID!, input: MemberProfileInput!)` — update member contact preferences

## Notes

Aetna does not currently publish a public GraphQL API. This schema is a conceptual representation of the business domain based on publicly documented REST, FHIR R4, and EDI capabilities. The schema is intended to guide API design discussions, developer portal enrichment, and interoperability planning.
