---
id: 02-package-boundaries
language: en-US
audience: agent
doc_type: spec
status: ready
owner: unassigned
branch:
pr:
files:
  - packages/
  - apps/
  - skills/
depends_on:
  - 01-workspace-tooling
claimed_at:
lease_expires_at:
updated: 2026-05-04
---

# Package Boundaries

## Scope

Create the initial ownership boundaries for protocol, daemon, CLI, web, and skill work.

## Plan

1. Create the expected directories.
2. Add minimal package metadata only when useful for validation.
3. Document dependency direction:
   - daemon and CLI may depend on protocol;
   - web may depend on protocol and renderer adapters;
   - protocol must not depend on web, OpenUI, daemon, or CLI.

## Validation

- Confirm package graph matches intended direction.
- Confirm no package introduces implementation dependencies before its spec requires them.
