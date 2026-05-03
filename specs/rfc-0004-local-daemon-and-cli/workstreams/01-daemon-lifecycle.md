---
id: 01-daemon-lifecycle
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
depends_on:
  - rfc-0002
  - rfc-0003
claimed_at:
lease_expires_at:
updated: 2026-05-04
---

# Daemon Lifecycle

## Scope

Implement local daemon startup, discovery, health checks, registry file handling, and local blackboard home creation.

## Validation

- Starting twice returns the same live daemon.
- Stale registry file is recovered cleanly.
- Health endpoint returns expected metadata.
