---
id: 02-run-surface-api
language: en-US
audience: agent
doc_type: spec
status: ready
owner: unassigned
branch:
pr:
files:
  - apps/daemon/
  - packages/protocol/
depends_on:
  - 01-daemon-lifecycle
claimed_at:
lease_expires_at:
updated: 2026-05-04
---

# Run And Surface API

## Scope

Expose local HTTP routes for run lifecycle, events, surfaces, artifacts, and actions.

## Validation

- Every write validates against protocol schemas.
- Stale surface revisions are handled as specified.
- Scoped clear/delete cannot cross run boundaries.
