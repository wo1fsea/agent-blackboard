---
id: 04-validation-fixtures
language: en-US
audience: agent
doc_type: spec
status: ready
owner: unassigned
branch:
pr:
files:
  - packages/protocol/
  - tests/
depends_on:
  - 01-protocol-schemas
  - 02-storage-schema
  - 03-lifecycle-and-revisions
claimed_at:
lease_expires_at:
updated: 2026-05-04
---

# Validation Fixtures

## Scope

Create representative protocol and storage fixtures that future daemon, CLI, and web work can reuse.

## Plan

1. Add valid run/surface/event/artifact/action fixtures.
2. Add invalid scope and stale revision fixtures.
3. Document fixture purpose near the test data.

## Validation

- Fixture tests pass.
- No fixture depends on OpenUI renderer behavior.
