---
id: 03-baseline-validation
language: en-US
audience: agent
doc_type: spec
status: ready
owner: unassigned
branch:
pr:
files:
  - package.json
  - packages/**/package.json
  - apps/**/package.json
depends_on:
  - 01-workspace-tooling
  - 02-package-boundaries
claimed_at:
lease_expires_at:
updated: 2026-05-04
---

# Baseline Validation

## Scope

Make validation commands discoverable and honest for a repo that has little implementation code yet.

## Plan

1. Add or confirm root validation commands.
2. Avoid green no-op checks unless they are named clearly.
3. Record what each command proves.
4. Leave a clear path for future specs to replace placeholders.

## Validation

- Run every new validation command.
- Record which commands are placeholders and why.
