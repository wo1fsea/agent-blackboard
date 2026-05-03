---
language: en-US
audience: agent
doc_type: spec
---

# Protocol And Storage Tech Spec

Product spec: `./PRODUCT.md`

## Context

`rfc-0002-mvp-scope-and-repo-scaffold` creates the workspace layout. This spec should be implemented after the scaffold because it owns `packages/protocol` and the storage layer used by the daemon.

The current platform model from `AGENTS.md` is `workspace`, `thread`, `run`, `surface`, `event`, `artifact`, and `action`. OpenUI remains a surface payload type, not a platform dependency.

## Change Gate

- Problem: daemon, CLI, web, and skill need a shared contract before implementation.
- Existing path considered: define payloads inline in daemon handlers.
- Why existing path is insufficient: inline shapes would drift across CLI, daemon, web, fixtures, and docs.
- Smallest new surface: versioned protocol schemas, TypeScript types, SQLite schema, storage repository interfaces.
- What will be deleted or replaced: any temporary inline payload definitions introduced during scaffold work.
- Owner: protocol/storage workstream owner.
- Validation: schema unit tests, storage migration tests, fixture round-trips.
- Temporary or permanent: permanent contract with future compatibility notes.
- Removal condition: replacement requires a new protocol migration spec.

## Proposed Changes

- Add `packages/protocol` with schemas and exported types.
- Define entity schemas:
  - workspace;
  - thread;
  - run;
  - surface;
  - event;
  - artifact;
  - action.
- Define surface payload variants:
  - `openui-page`;
  - `markdown`;
  - `artifact-list`.
- Define event categories:
  - lifecycle;
  - status;
  - timeline;
  - surface;
  - artifact;
  - action.
- Add SQLite tables for durable local state.
- Add storage helpers or repository functions behind the daemon boundary.
- Add fixtures for valid payloads, stale revisions, invalid scopes, and lifecycle operations.

## Workstream Split

- `01-protocol-schemas`: Zod schemas, TypeScript types, fixtures.
- `02-storage-schema`: SQLite schema, migrations, repository shape.
- `03-lifecycle-and-revisions`: lifecycle operations and conflict handling.
- `04-validation-fixtures`: tests and sample payloads.

## Testing And Validation

- Schema validation tests for every public payload.
- Fixture round-trip tests for JSON serialization.
- SQLite migration or initialization test.
- Stale revision conflict test.
- Scoped clear/delete test proving cross-run data is not removed.

## Risks And Follow-Ups

- Thread id discovery may require daemon or CLI support. Keep the schema flexible while requiring a stable thread identifier string.
- Artifact policy may need tightening once file upload/copy behavior is implemented.
- Future AG-UI/A2UI adapters should map into these schemas instead of replacing them.
