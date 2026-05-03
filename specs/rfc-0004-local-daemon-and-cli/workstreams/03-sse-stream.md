---
id: 03-sse-stream
language: en-US
audience: agent
doc_type: spec
status: ready
owner: unassigned
branch:
pr:
files:
  - apps/daemon/
depends_on:
  - 02-run-surface-api
claimed_at:
lease_expires_at:
updated: 2026-05-04
---

# SSE Stream

## Scope

Expose daemon events to local web clients through Server-Sent Events.

## Validation

- Connected clients receive events after writes.
- Closed clients are cleaned up.
- Stream reconnect can recover through latest durable state.
