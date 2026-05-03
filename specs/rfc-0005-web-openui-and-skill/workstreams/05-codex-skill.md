---
id: 05-codex-skill
language: en-US
audience: agent
doc_type: spec
status: ready
owner: unassigned
branch:
pr:
files:
  - skills/agent-blackboard/
depends_on:
  - rfc-0004
  - 02-openui-renderer
  - 03-component-catalog
  - 04-actions-ui
claimed_at:
lease_expires_at:
updated: 2026-05-04
---

# Codex Skill

## Scope

Create the `agent-blackboard` skill that teaches agents how to use the daemon and CLI without loading platform internals into context.

## Validation

- Skill `SKILL.md` stays concise.
- Examples can drive `displayctl` against a local daemon.
- References are loaded only when needed.
