# Bureau of Industry and Security (bureau-of-industry-and-security)

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

The Bureau of Industry and Security (BIS), a division of the U.S. Department of Commerce, advances U.S. national security, foreign policy, and economic objectives by administering an effective export control and treaty compliance system. BIS maintains the Commerce Control List (CCL), administers the Consolidated Screening List (CSL), and operates the SNAP-R licensing system.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/bureau-of-industry-and-security/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/bureau-of-industry-and-security/refs/heads/main/apis.yml)

## Scope

- **Type:** Index
- **Position:** Consumer
- **Access:** 3rd-Party

## Tags

- Compliance
- Export Controls
- Federal Government
- Industries
- National Security
- Screening Lists
- Security

## Timestamps

- **Created:** 2024-11-25
- **Modified:** 2026-04-21

## APIs

### Consolidated Screening List (CSL) API

The Consolidated Screening List (CSL) API consolidates export screening lists from the Departments of Commerce, State, and Treasury. It includes the Entity List, Denied Persons List, Unverified List (BIS), ITAR Debarred List (State), SDN List, and others. Used for trade compliance and due diligence screening.

- **Human URL:** [https://www.trade.gov/consolidated-screening-list](https://www.trade.gov/consolidated-screening-list)
- **Base URL:** `https://api.trade.gov/gateway/v1/consolidated_screening_list`

#### Tags

- Compliance
- Export Controls
- Federal Government
- Sanctions
- Screening

#### Properties

- [Documentation](https://www.trade.gov/consolidated-screening-list)
- [Data A P I](https://api.trade.gov/gateway/v1/consolidated_screening_list/search)
- [Postman Collection](collections/bureau-of-industry-and-security.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/bureau-of-industry-and-security.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### SNAP-R Export License Application System

SNAP-R (Simplified Network Application Process Redesign) is the BIS online system for applying for export licenses, classifications, and authorizations under the Export Administration Regulations (EAR).

- **Human URL:** [https://snapr.bis.doc.gov/](https://snapr.bis.doc.gov/)

#### Tags

- Export Controls
- Federal Government
- Licensing

#### Properties

- [Documentation](https://www.bis.gov/licensing/how-to-apply-snap-r)
- [Postman Collection](collections/bureau-of-industry-and-security.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/bureau-of-industry-and-security.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### STELA Export License Tracking

STELA (System for Tracking Export License Applications) allows applicants to check the status of export license applications submitted to BIS.

- **Human URL:** [https://www.bis.gov/licensing/stela](https://www.bis.gov/licensing/stela)

#### Tags

- Export Controls
- Federal Government
- Licensing
- Tracking

#### Properties

- [Documentation](https://www.bis.gov/licensing/stela)
- [Postman Collection](collections/bureau-of-industry-and-security.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/bureau-of-industry-and-security.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [LinkedIn](https://www.linkedin.com/company/bureau-of-industry-and-security-u-s-department-of-commerce)
- [Website](https://www.bis.gov)
- [Privacy Policy](https://www.bis.gov/privacy-policy)
- [Consolidated  Screening  List](https://www.trade.gov/consolidated-screening-list)
- [Export  Administration  Regulations](https://www.bis.gov/regulations/export-administration-regulations-ear)
- [Commerce  Control  List](https://www.bis.gov/regulations/commerce-control-list-ccl)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
