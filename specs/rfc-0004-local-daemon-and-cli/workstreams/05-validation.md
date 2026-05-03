---
id: 05-validation
language: en-US
audience: agent
doc_type: spec
status: ready
owner: unassigned
branch:
pr:
files:
  - apps/daemon/
  - packages/cli/
  - tests/
depends_on:
  - 01-daemon-lifecycle
  - 02-run-surface-api
  - 03-sse-stream
  - 04-displayctl
claimed_at:
lease_expires_at:
updated: 2026-05-04
---

# Validation

## Scope

Add tests and smoke checks that prove daemon and CLI behavior.

## Validation

- Automated tests pass.
- Manual smoke flow recorded when process management cannot be fully automated.
