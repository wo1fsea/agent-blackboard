---
id: 04-docs
language: en-US
audience: agent
doc_type: spec
status: ready
owner: unassigned
branch:
pr:
files:
  - README.md
  - AGENTS.md
  - specs/rfc-0002-mvp-scope-and-repo-scaffold/
depends_on:
  - 01-workspace-tooling
  - 02-package-boundaries
  - 03-baseline-validation
claimed_at:
lease_expires_at:
updated: 2026-05-04
---

# Docs

## Scope

Update durable documentation so future agents know how to use the scaffold and what remains intentionally unimplemented.

## Plan

1. Update README with install and validation commands.
2. Update specs if implementation changes package manager, layout, or command names.
3. Record residual risks in `STATUS.md`.

## Validation

- Confirm links and command names are correct.
- Confirm durable docs include language, audience, and doc_type metadata.
