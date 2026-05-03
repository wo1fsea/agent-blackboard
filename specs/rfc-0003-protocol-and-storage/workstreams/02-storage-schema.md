---
id: 02-storage-schema
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
  - 01-protocol-schemas
claimed_at:
lease_expires_at:
updated: 2026-05-04
---

# Storage Schema

## Scope

Design the SQLite schema and storage helper boundaries for local durable state.

## Plan

1. Add tables for workspaces, threads, runs, surfaces, events, artifacts, and actions.
2. Store events append-only.
3. Store current surface snapshots with revision numbers.
4. Keep migration or initialization logic deterministic.

## Validation

- SQLite initialization test.
- Basic insert/read tests for each entity.
