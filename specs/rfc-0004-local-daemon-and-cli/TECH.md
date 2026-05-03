---
language: en-US
audience: agent
doc_type: spec
---

# Local Daemon And CLI Tech Spec

Product spec: `./PRODUCT.md`

## Context

This spec depends on `rfc-0002-mvp-scope-and-repo-scaffold` and `rfc-0003-protocol-and-storage`. The daemon and CLI should consume protocol schemas instead of defining their own payload shapes.

The recommended architecture from project notes is Hono + Node for the daemon, HTTP writes, SSE reads, SQLite persistence, and a `displayctl` CLI.

## Change Gate

- Problem: agents need a mechanical surface to write progress and pages outside chat.
- Existing path considered: write JSON files directly from the skill.
- Why existing path is insufficient: direct files would make concurrency, revisions, SSE, and future UI integration brittle.
- Smallest new surface: localhost daemon, local HTTP API, `displayctl` commands, daemon registry file.
- What will be deleted or replaced: temporary manual JSON-writing helpers, if any.
- Owner: daemon/CLI workstream owners.
- Validation: CLI smoke tests, API tests, SSE test, storage integration tests.
- Temporary or permanent: permanent local API; command names become public project surface.
- Removal condition: command or endpoint changes require a migration spec.

## Proposed API Shape

Initial route names may change during implementation, but the capability set should remain:

- `GET /health`
- `POST /runs`
- `PATCH /runs/:runId`
- `POST /runs/:runId/events`
- `POST /runs/:runId/surfaces`
- `PATCH /runs/:runId/surfaces/:surfaceId`
- `POST /runs/:runId/artifacts`
- `GET /runs/:runId/actions`
- `PATCH /runs/:runId/actions/:actionId`
- `GET /events/stream`

## Proposed CLI Shape

- `displayctl up`
- `displayctl begin --title <title>`
- `displayctl status <message>`
- `displayctl event --type <type> --message <message>`
- `displayctl page create --id <surface-id>`
- `displayctl page patch --id <surface-id> --stdin`
- `displayctl artifact add <path-or-url>`
- `displayctl action wait --run <run-id> --timeout <seconds>`
- `displayctl complete`
- `displayctl clear --run <run-id>`

## Workstream Split

- `01-daemon-lifecycle`: startup, registry, health, local storage home.
- `02-run-surface-api`: run, event, surface, artifact, action APIs.
- `03-sse-stream`: event stream for web clients.
- `04-displayctl`: CLI commands and skill-friendly output.
- `05-validation`: tests and smoke checks.

## Testing And Validation

- Daemon health smoke test.
- Idempotent `displayctl up` test.
- Begin/status/page/artifact/complete CLI flow test.
- API schema rejection test.
- SSE emits after a write.
- Scoped clear/delete test.

## Risks And Follow-Ups

- Daemon process management can vary across OS environments. Keep v1 macOS/Linux local-first unless implementation proves otherwise.
- CLI output must be stable enough for a skill to use, so JSON output should be available where useful.
- True push callbacks into Codex are out of scope; action wait/poll commands are enough for MVP.
