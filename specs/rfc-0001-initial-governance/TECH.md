---
language: en-US
audience: agent
doc_type: spec
---

# Initial Governance Tech Spec

Product spec: `./PRODUCT.md`

## Context

The repository currently contains initial project notes only. It needs repo-local guidance before agent-driven implementation starts because future work will likely include public protocol surface, local daemon behavior, persisted state, OpenUI rendering, CLI commands, and a Codex skill.

## Proposed Changes

- Initialize Code & Order with the universal suite and strict TDD mode.
- Keep `AGENTS.md` as the canonical router while preserving project-specific intent and guardrails.
- Add thin adapter files:
  - `CLAUDE.md`
  - `GEMINI.md`
  - `.github/copilot-instructions.md`
- Add governance workflows under `docs/governance/`.
- Add starter spec files under `specs/rfc-0001-initial-governance/`.
- Track provenance with `docs/governance/code-and-order.lock.json`.

## Testing and Validation

- Run Code & Order audit after initialization.
- Inspect generated files for stale placeholders.
- Confirm `AGENTS.md` routes to all generated governance docs.
- Confirm git status contains only scoped governance changes.

## Risks and Follow-ups

- The lockfile will track generated templates while `AGENTS.md` and starter specs are intentionally customized for this project.
- Canonical validation commands remain unavailable until the code scaffold exists.
- A future scaffold spec should choose package manager, workspace layout, and first CI commands.
