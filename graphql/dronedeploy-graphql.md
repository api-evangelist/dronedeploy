# DroneDeploy GraphQL API

DroneDeploy is a drone mapping, reality capture, and aerial analytics platform. Its
developer platform is a single **GraphQL API** that lets Enterprise and Developer
Partner accounts create, read, and update DroneDeploy data - organizations, projects,
map plans, exports, annotations/issues, images, and webhooks - through one strongly
typed, Relay-style schema rooted at the `viewer` object.

**Endpoint:** `https://www.dronedeploy.com/graphql` (POST)
**Explorer (GraphiQL):** https://www.dronedeploy.com/graphiql/
**Authentication:** `Authorization: Bearer <api_key>` (API key is per-user; obtained from
DroneDeploy Sales/Support for Enterprise or Developer Partner accounts)
**Pagination:** Relay cursor connections - `first`, `after`, `pageInfo { hasNextPage endCursor }`,
`edges { cursor node { ... } }`

## Confirmed operations (from the public developer docs)

- `viewer` root object returning the current user (e.g. `username`) and `organization`.
- `viewer.organization.plans(first, after)` - cursor-paginated MapPlan connection.
- `node(id: "MapPlan:<id>")` returning the `Node` interface, resolved with `... on MapPlan`.
- `MapPlan` fields: `name`, `location { lat lng }`, `geometry { lat lng }`, `dateCreation`,
  `imageCount`, `status`, and `exports(first, after)`.
- `Export` fields: `id`, `user { username }`, `parameters { projection merge contourInterval
  fileFormat resolution layer webhook { url } }`, `status`, `dateCreation`, `downloadPath`.
- `createExport(input: CreateExportInput!)` mutation - `CreateExportInput` requires `planId`
  and `parameters` (only `layer` required within parameters; optional `webhook.url` is called
  when the export reaches `COMPLETE`).
- `Issue` type and its input types (e.g. `UpdateIssueInput`) for annotations/markups.

## Modeled operations

Fields and mutations for project/plan creation, image upload, annotation creation, reports,
member management, and standalone webhook subscriptions are **modeled** in the accompanying
schema file from the schema's `QueryRoot`/`MutationRoot` structure and the platform's
documented features. The full introspected schema is gated behind the Enterprise GraphiQL
console; verify exact field shapes there.

- Reference: https://developer-docs.dronedeploy.com/api/introduction
- Examples: https://developer-docs.dronedeploy.com/api/examples
- Schema: graphql/dronedeploy-schema.graphql
