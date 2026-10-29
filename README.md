# DroneDeploy

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

DroneDeploy is a drone mapping, reality capture, and aerial analytics platform for construction, energy, agriculture, and inspection. Its developer platform is a GraphQL API (endpoint https://www.dronedeploy.com/graphql) that lets Enterprise and Developer Partner accounts query and mutate DroneDeploy data - organizations, projects, map plans, exports, annotations/issues, images, and webhooks - using a single strongly typed, Relay-style (cursor-paginated) schema rooted at the `viewer` object. A set of legacy REST APIs (Map Processing / Map Engine as a Service, Plan API, Export API) also remains available, but DroneDeploy recommends the GraphQL API for most integrations.

**Areas:** Drone Mapping · Reality Capture · Aerial Analytics · Geospatial · GraphQL · Photogrammetry

## DroneDeploy on APIs.io

Everything profiled for DroneDeploy is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/dronedeploy/](https://apis.io/providers/dronedeploy/)** — or go straight to one of the APIs or properties below.

### APIs (7)

- [DroneDeploy Projects and Plans API](https://apis.io/apis/dronedeploy/dronedeploy-projects-and-plans-api/) — Query the projects and plans (MapPlan) in an organization through `viewer.organization.plans`/`projects` and the `node(id)` lookup - reading name, location…
- [DroneDeploy Maps and Exports API](https://apis.io/apis/dronedeploy/dronedeploy-maps-and-exports-api/) — Generate and retrieve map exports from a MapPlan. The confirmed `createExport(input CreateExportInput!)` mutation takes a planId plus parameters (layer…
- [DroneDeploy Annotations and Issues API](https://apis.io/apis/dronedeploy/dronedeploy-annotations-and-issues-api/) — Create, read, and update annotations and Issues (field markups tied to a plan's map - points, lines, polygons, and their notes/attachments) through the…
- [DroneDeploy Uploads and Images API](https://apis.io/apis/dronedeploy/dronedeploy-uploads-and-images-api/) — Manage the source imagery behind a map. `MapPlan.imageCount` is confirmed; image listing and upload/ingest mutations that add photos to a plan and trigger…
- [DroneDeploy Users and Organizations API](https://apis.io/apis/dronedeploy/dronedeploy-users-and-organizations-api/) — Resolve the authenticated account and its organization. The confirmed `viewer` root returns the current user (e.g. username) and `viewer.organization`…
- [DroneDeploy Reports API](https://apis.io/apis/dronedeploy/dronedeploy-reports-api/) — Retrieve analytic and reporting artifacts derived from a plan - volume/stockpile measurements, cut/fill, and generated report documents. Reports are…
- [DroneDeploy Webhooks API](https://apis.io/apis/dronedeploy/dronedeploy-webhooks-api/) — Register outbound webhooks so DroneDeploy notifies your endpoint when long-running work finishes. Confirmed on the export flow, where a `webhook.url` set…

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### GraphQL (1)

GraphQL schemas.

- [DroneDeploy GraphQL API](https://apis.io/graphqls/dronedeploy/dronedeploy-graphql/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [dronedeploy](https://apis.io/servers/dronedeploy/dronedeploy/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Dronedeploy Agentic Access](https://apis.io/agentic-access/dronedeploy/dronedeploy-agentic-access/)

#### Collections (1)

Postman and Open Collection request collections.

- [DroneDeploy GraphQL API](https://apis.io/collections/dronedeploy/open-dronedeploy/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Dronedeploy Authentication](https://apis.io/security/dronedeploy/dronedeploy-authentication/)
- [Dronedeploy Domain Security](https://apis.io/security/dronedeploy/dronedeploy-domain-security/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Dronedeploy Plans Pricing](https://apis.io/plans/dronedeploy/dronedeploy-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Dronedeploy Rate Limits](https://apis.io/rate-limits/dronedeploy/dronedeploy-rate-limits/)

#### FinOps (1)

What the API costs to run, by operation.

- [Dronedeploy Finops](https://apis.io/finops/dronedeploy/dronedeploy-finops/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.dronedeploy.com/)
- [Documentation](https://developer-docs.dronedeploy.com/api/introduction)
- [Support](https://help.dronedeploy.com/hc/en-us)
- [Blog](https://www.dronedeploy.com/blog)
- [Terms of service](https://www.dronedeploy.com/legal/master-services-agreement)
- [Privacy policy](https://www.dronedeploy.com/legal/privacy)
- [GitHub](https://github.com/dronedeploy)
- [Status](https://status.dronedeploy.com)

## API Evangelist rating

**Kin Score 29.9** — thin · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 73.3 |
| Contract quality | 0.0 |
| Contract governance | 0.0 |
| Operational transparency | 26.3 |
| Developer ergonomics | 56.7 |
| Access clarity | 35.5 |

**Agent readiness 17.2** — agent-aware

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | — |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | verified |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | — |
| OpenAPI Examples | — |
| Rate Limit Signal | derived (partial credit) |
| Event Surface Described | — |
| Agent Skills | — |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | verified |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | na |
| Operation Distinctiveness | na |

**Regulatory alignment 19.6** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/dronedeploy/](https://apis.io/providers/dronedeploy/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for DroneDeploy: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/dronedeploy/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
