---
id: 04-displayctl
language: en-US
audience: agent
doc_type: spec
status: ready
owner: unassigned
branch:
pr:
files:
  - packages/cli/
depends_on:
  - 01-daemon-lifecycle
  - 02-run-surface-api
claimed_at:
lease_expires_at:
updated: 2026-05-04
---

# displayctl

## Scope

Implement the CLI surface used by humans, Codex, and the future skill.

## Validation

- CLI smoke flow covers `up`, `begin`, `status`, `page`, `artifact`, and `complete`.
- JSON output exists for commands the skill will parse.
- Errors are concise and actionable.
