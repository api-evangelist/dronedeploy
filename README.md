# DroneDeploy (dronedeploy)

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
