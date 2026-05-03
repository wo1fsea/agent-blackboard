---
id: 03-lifecycle-and-revisions
language: en-US
audience: agent
doc_type: spec
status: ready
owner: unassigned
branch:
pr:
files:
  - packages/protocol/
  - apps/daemon/
depends_on:
  - 01-protocol-schemas
  - 02-storage-schema
claimed_at:
lease_expires_at:
updated: 2026-05-04
---

# Lifecycle And Revisions

## Scope

Specify and implement state transitions for runs, surfaces, artifacts, actions, and data cleanup.

## Plan

1. Define run lifecycle values.
2. Define surface create, replace, patch, archive, and delete behavior.
3. Define conflict behavior for stale surface revisions.
4. Define scoped clear/delete semantics.

## Validation

- Stale revision conflict test.
- Run completion and action expiration test.
- Scoped cleanup test.
