---
id: 01-protocol-schemas
language: en-US
audience: agent
doc_type: spec
status: ready
owner: unassigned
branch:
pr:
files:
  - packages/protocol/
depends_on:
  - rfc-0002
claimed_at:
lease_expires_at:
updated: 2026-05-04
---

# Protocol Schemas

## Scope

Define versioned payload schemas and TypeScript types for the platform model.

## Plan

1. Define entity identifiers and timestamps.
2. Define workspace/thread/run/surface/event/artifact/action schemas.
3. Define supported MVP surface payload variants.
4. Add fixtures for valid and invalid payloads.

## Validation

- Run schema tests.
- Verify fixtures parse and serialize.
