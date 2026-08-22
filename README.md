# DroneDeploy (dronedeploy)

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

DroneDeploy is a drone mapping, reality capture, and aerial analytics platform for construction, energy, agriculture, and inspection. Its developer platform is a **GraphQL API** (endpoint `https://www.dronedeploy.com/graphql`) that lets Enterprise and Developer Partner accounts query and mutate DroneDeploy data - organizations, projects, map plans, exports, annotations/issues, images, and webhooks - through one strongly typed, Relay-style (cursor-paginated) schema rooted at the `viewer` object and resolved by `node(id)`. A set of legacy REST APIs (Map Processing / Map Engine as a Service, Plan API, Export API) also remains available, but DroneDeploy recommends the GraphQL API for most integrations.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/dronedeploy/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/dronedeploy/refs/heads/main/apis.yml)

## Tags

- Drone Mapping
- Reality Capture
- Aerial Analytics
- Geospatial
- GraphQL
- Photogrammetry

## Timestamps

- **Created:** 2026-07-04
- **Modified:** 2026-07-04

## Authentication & Access

- **Endpoint:** `https://www.dronedeploy.com/graphql` (POST)
- **Explorer:** https://www.dronedeploy.com/graphiql/
- **Auth:** `Authorization: Bearer <api_key>` — API keys are issued only to Enterprise or Developer Partner accounts via DroneDeploy Sales/Support.
- **Pagination:** Relay cursor connections — `first` / `after`, `pageInfo { hasNextPage endCursor }`, `edges { cursor node }`.

## APIs

### DroneDeploy Projects and Plans API

Query the projects and plans (MapPlan) in an organization through `viewer.organization.plans`/`projects` and the `node(id)` lookup — name, location and geometry (lat/lng), dateCreation, imageCount, and status — with cursor pagination. Creation/update mutations are modeled.

- **Human URL:** [Fetching all Plans](https://developer-docs.dronedeploy.com/api/examples/fetching-all-plans-for-your-organization)
- **Base URL:** `https://www.dronedeploy.com/graphql`
- Tags: Projects, Plans, MapPlan, GraphQL

### DroneDeploy Maps and Exports API

Generate and retrieve map exports from a MapPlan. The confirmed `createExport(input: CreateExportInput!)` mutation takes a planId plus parameters (layer required; projection, merge, contourInterval, fileFormat, resolution, optional completion webhook) and returns an export id; `MapPlan.exports` returns status, dateCreation, and downloadPath once processing reaches COMPLETE.

- **Human URL:** [Creating an Export](https://developer-docs.dronedeploy.com/api/examples/creating-an-export)
- **Base URL:** `https://www.dronedeploy.com/graphql`
- Tags: Maps, Exports, Reality Capture, GraphQL

### DroneDeploy Annotations and Issues API

Create, read, and update annotations and Issues (field markups tied to a plan — points, lines, polygons, notes/attachments) via the schema's Issue type and its input types (e.g. `UpdateIssueInput`). Modeled; field shapes are gated behind the Enterprise console.

- **Human URL:** [API Introduction](https://developer-docs.dronedeploy.com/api/introduction)
- **Base URL:** `https://www.dronedeploy.com/graphql`
- Tags: Annotations, Issues, Markups, GraphQL

### DroneDeploy Uploads and Images API

Manage the source imagery behind a map. `MapPlan.imageCount` is confirmed; image listing and upload/ingest mutations (which trigger map processing) are modeled. Large binaries follow DroneDeploy's presigned-upload flow rather than inline GraphQL payloads.

- **Human URL:** [API Introduction](https://developer-docs.dronedeploy.com/api/introduction)
- **Base URL:** `https://www.dronedeploy.com/graphql`
- Tags: Uploads, Images, Photogrammetry, GraphQL

### DroneDeploy Users and Organizations API

Resolve the authenticated account and its organization. The confirmed `viewer` root returns the current user (e.g. username) and `viewer.organization` exposes the org and its plans/projects collections. Member/role management fields are modeled.

- **Human URL:** [Authentication](https://developer-docs.dronedeploy.com/api/authentication)
- **Base URL:** `https://www.dronedeploy.com/graphql`
- Tags: Users, Organizations, Viewer, GraphQL

### DroneDeploy Reports API

Retrieve analytic and reporting artifacts derived from a plan — volume/stockpile measurements, cut/fill, and generated report documents — surfaced as a specialized export/report layer on MapPlan. Report types and mutations are modeled from the export schema and platform features.

- **Human URL:** [API Introduction](https://developer-docs.dronedeploy.com/api/introduction)
- **Base URL:** `https://www.dronedeploy.com/graphql`
- Tags: Reports, Analytics, Exports, GraphQL

### DroneDeploy Webhooks API

Register outbound webhooks so DroneDeploy notifies your endpoint when long-running work finishes. Confirmed on the export flow, where a `webhook.url` in CreateExportInput parameters is called when the export is COMPLETE. A standalone Webhook type exists; subscribe/manage mutations are modeled.

- **Human URL:** [Creating an Export](https://developer-docs.dronedeploy.com/api/examples/creating-an-export)
- **Base URL:** `https://www.dronedeploy.com/graphql`
- Tags: Webhooks, Events, Notifications, GraphQL

## Artifacts

- [GraphQL Overview](graphql/dronedeploy-graphql.md)
- [GraphQL Schema (partial / modeled)](graphql/dronedeploy-schema.graphql)
- [Postman Collection](collections/dronedeploy.postman_collection.json)
- [Open Collection](collections/dronedeploy.opencollection.json)
- [Plans & Pricing](plans/dronedeploy-plans-pricing.yml)
- [Rate Limits](rate-limits/dronedeploy-rate-limits.yml)
- [FinOps](finops/dronedeploy-finops.yml)
- [Review](review.yml)

## Common Properties

- [GitHub Organization](https://github.com/dronedeploy)
- [LinkedIn](https://www.linkedin.com/company/dronedeploy)
- [Website](https://www.dronedeploy.com/)
- [Documentation](https://developer-docs.dronedeploy.com/api/introduction)
- [Plans](plans/dronedeploy-plans-pricing.yml)
- [Rate Limits](rate-limits/dronedeploy-rate-limits.yml)
- [Fin Ops](finops/dronedeploy-finops.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
