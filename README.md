# Certn (certn-com)

Certn is a Canadian background screening platform headquartered in Victoria, British Columbia, providing fast, FCRA / SOC 2 Type II / ISO 27001 compliant background checks for employment, tenant, and partner screening across more than 195 countries. The platform delivers criminal record checks (Canadian Basic and Enhanced, SOQUIJ Quebec, international), identity verification (OneID across 13,500+ document types), employment, education, and credential verification, credit reports, public records and social media screening, reference checks, driver's abstract / MVR, and white-label candidate experiences. Certn exposes a REST API used by 100+ ATS / HRIS partners (Workable, Greenhouse, Lever, Workday and others) to embed screening directly into hiring and leasing workflows, with signed webhook callbacks for asynchronous result delivery.

**URL:** [Visit APIs.json](https://raw.githubusercontent.com/api-evangelist/certn-com/refs/heads/main/apis.yml)

**Run:** [Capabilities Using Naftiko](https://github.com/naftiko/fleet?utm_source=api-evangelist&utm_medium=readme&utm_campaign=company-api-evangelist&utm_content=repo)

## Tags

- Background Checks, Background Screening, Identity Verification, Criminal Record Checks, Employment Verification, Education Verification, Credential Verification, Credit Checks, Reference Checks, Tenant Screening, Property Management, Human Resources, HR Tech, Compliance, FCRA, SOC 2, ISO 27001, Canada

## Timestamps

- **Created:** 2026-05-25
- **Modified:** 2026-05-25

## API Surface

Certn currently runs two API generations in parallel. The legacy v1/v2 API was deprecated on **2026-04-13** and will be retired on **2026-08-05**. The new **CertnCentric API** is the recommended integration path going forward.

| API | Base | Status |
|---|---|---|
| Certn HR API (v1) | `https://api.certn.co/hr/v1/` | Deprecated — retires 2026-08-05 |
| Certn Property Management API (v2) | `https://api.certn.co/api/v2/` | Deprecated — retires 2026-08-05 |
| CertnCentric API | `https://api.certn.co` | Current |
| Certn Webhooks | Customer-defined endpoint | Current |

Demo / sandbox base URL: `https://demo-api.certn.co`. Authentication uses bearer tokens; published rate limits are 120 requests / minute burst and 14,400 requests / 24h sustained.

## APIs

### Certn HR API (Legacy v1)

Human Resources surface of the legacy Certn API used to invite applicants to a hosted screening application, run instant "quick" screens, add package items to existing applicants, and list applications for a team account.

**Human URL:** [https://docs.certn.co/api/certn-api-v-1.0/api-reference/hr](https://docs.certn.co/api/certn-api-v-1.0/api-reference/hr)

| Method | Path | Purpose |
|---|---|---|
| POST | `/hr/v1/applications/invite/` | Send an invitation to an applicant to complete a screening application |
| POST | `/hr/v1/applications/quick/` | Run an immediate screening from the request body |
| PUT | `/hr/v1/applicants/{applicant_id}/packages/` | Add additional checks to an existing applicant |
| GET | `/hr/v1/applicants/` | List paginated applications for the team |

### Certn Property Management API (Legacy v2)

Property Management surface for tenant screening. Same shape as the HR API but rooted at `/api/v2/`.

**Human URL:** [https://docs.certn.co/api/certn-api-v-1.0/api-reference/pm](https://docs.certn.co/api/certn-api-v-1.0/api-reference/pm)

| Method | Path | Purpose |
|---|---|---|
| POST | `/api/v2/applications/invite/` | Invite an applicant to complete a tenant screen |
| POST | `/api/v2/applications/quick` | Run an instant tenant screen |
| PUT | `/api/v2/applicants/{applicant_id}/packages/` | Add screening requests to an existing application |
| GET | `/api/v2/applicants/` | List paginated applications |

### CertnCentric API

Next-generation unified Certn screening API replacing the deprecated v1/v2 industry-split surfaces. The CertnCentric REST API consolidates HR and PM workflows into a single contract for embedding background checks (criminal, identity, employment, education, credit, references, MVR, public records, social media) into ATS, HRIS, and property management workflows.

**Human URL:** [https://centric-api-docs.certn.co/](https://centric-api-docs.certn.co/)

- [Documentation — CertnCentric Developer Reference](https://centric-api-docs.certn.co/)
- [Documentation — Introduction](https://centric-api-docs.certn.co/#introduction)

### Certn Webhooks

Outbound webhook delivery for asynchronous screening events. Certn POSTs JSON payloads containing applicant `status`, `result`, `check_executions`, `enhanced_identity_verification`, `rcmp_result`, `information`, and `activity_log` to a customer-configured endpoint set in team settings.

Payloads are signed with an HMAC-SHA256 `Certn-Signature` header carrying a timestamped signature in the form `t=<timestamp>,v1=<signature>` to prevent replay attacks.

**Human URL:** [https://docs.certn.co/api/certn-api-v-1.0/guides/use-the-api/webhooks](https://docs.certn.co/api/certn-api-v-1.0/guides/use-the-api/webhooks)

## Check Types and Pricing (CAD, self-serve)

| Check | Price | Turnaround |
|---|---|---|
| OneID Identity Verification | $4.99 | Instant |
| Digital Reference Check | $4.49 | Asynchronous |
| Public Records Check | $9.99 | < 1 hour |
| Credit Report | $12.99 | Instant |
| Canadian Basic Criminal Record Check | $24.99 | 4–72 hours |
| Canadian Enhanced Criminal Record Check | $29.99 | 4–72 hours |
| Employment Verification | $29.99 | Varies |
| Education Verification | $29.99 | Varies |
| Credential Verification | $29.99 | Varies |
| Driver's Abstract / MVR | $35.99 | Varies |
| Quebec SOQUIJ Record Check | $39.99 | ~1 day |
| Phone Reference Check | $39.99 | Asynchronous |
| Social Media Check | $59.99 | 1–2 days |

Enterprise pricing is custom — see [certn.co/request-a-quote](https://certn.co/request-a-quote/).

## Features

- Canadian Basic and Enhanced criminal record checks with RCMP-aligned results
- Quebec SOQUIJ record checks
- International criminal background checks across 200+ countries and territories
- OneID identity verification supporting 13,500+ government document types
- Employment, education, and professional credential verification
- Credit report and public records checks
- Social media screening
- Phone and digital reference checks
- Driver's abstract / motor vehicle records (MVR) checks
- Personal background checks via the mycrc.ca consumer brand
- White-label candidate experience embeddable in customer ATS/HRIS
- 100+ pre-built integrations including Workable, Greenhouse, Lever, Workday
- REST API with token authentication and a `demo-api.certn.co` sandbox environment
- Outbound webhooks with HMAC-SHA256 signed payloads (`Certn-Signature`) and replay protection
- Rate limits — 120 requests / minute burst, 14,400 requests / 24h sustained
- FCRA, SOC 2 Type II, and ISO 27001 compliance posture

## Common Resources

- [Website](https://certn.co)
- [Background Screening API portal](https://certn.co/background-screening-api/)
- [API Documentation (legacy)](https://docs.certn.co/api)
- [API Documentation (CertnCentric)](https://centric-api-docs.certn.co/)
- [Pricing](https://certn.co/pricing/)
- [Sign In](https://client.certn.co/ca/login)
- [Personal background checks (mycrc.ca)](https://mycrc.ca)
- [Blog](https://certn.co/blog/)
- [Privacy Policy](https://certn.co/privacy-policy/)
- [Contact](https://certn.co/contact/)
- [Careers](https://certn.co/careers/)
- [Trust Center](https://trust.certn.co/)
- [Help Center / Support](https://certn.zendesk.com/hc/en-us)
- [Partner Marketplace](https://certn.co/partner-marketplace/)
- [GitHub Organization](https://github.com/certn)
- [LinkedIn](https://www.linkedin.com/company/certn)
- [Workable integration guide](https://help.workable.com/hc/en-us/articles/360017580593-Integrating-with-Certn)

## Maintainers

- **Kin Lane** — kin@apievangelist.com — [apievangelist.com](https://apievangelist.com)
