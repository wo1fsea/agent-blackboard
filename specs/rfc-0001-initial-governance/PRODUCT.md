---
language: en-US
audience: mixed
doc_type: spec
---

# Initial Governance Product Spec

## Summary

Initialize `agent-blackboard` with lightweight but strict Code & Order governance so humans and agents have a stable workflow before implementation begins.

## Goals

- Provide a canonical `AGENTS.md` router for all coding agents.
- Add thin adapters for Claude, Gemini, and GitHub Copilot.
- Add governance docs for development, change gates, documentation, validation, review, specs, TDD, temp artifacts, and multi-agent work.
- Create a starter spec structure so future feature work can begin from product intent, technical plan, status, and workstreams.
- Preserve the project's early intent: local-first Codex thread visualization, OpenUI page surfaces, and an eventual `agent-blackboard` skill.

## Non-Goals

- Do not implement the product runtime.
- Do not choose package manager, server framework, or frontend scaffold yet.
- Do not define final validation commands before the codebase exists.

## Behavior

1. Agents read `AGENTS.md` first and route to detailed workflows in `docs/governance/`.
2. Project work is spec-first by default.
3. TDD evidence is expected for behavior changes once implementation begins.
4. New project surface must pass the change gate before being added.
5. Durable docs must declare language, audience, and document type near the top.

## Open Questions

- Which package manager and workspace layout will the implementation use?
- Which commands will become canonical for format, lint, typecheck, test, build, and UI validation?
