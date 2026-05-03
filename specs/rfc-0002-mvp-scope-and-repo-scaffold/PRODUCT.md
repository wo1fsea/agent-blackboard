---
language: en-US
audience: mixed
doc_type: spec
---

# MVP Scope And Repo Scaffold Product Spec

## Summary

Create the first implementation scaffold for `agent-blackboard`: a local-first TypeScript workspace that can later host the protocol package, local daemon, CLI, web UI, and Codex skill.

This spec is intentionally about boundaries and build surface, not product runtime behavior. It prevents the first code change from mixing scaffold decisions with protocol, daemon, and UI implementation.

## Goals

- Establish a predictable repository layout for the MVP.
- Add discoverable package scripts for validation and development.
- Keep the platform kernel independent from OpenUI and any future renderer.
- Make future workstreams small enough for agents to claim independently.
- Preserve a local-first default and defer remote/multi-machine concerns.

## Non-Goals

- Do not implement the daemon API.
- Do not implement storage schema or persistence.
- Do not render OpenUI pages.
- Do not create arbitrary sandbox app support.
- Do not add CI until baseline local commands exist.

## Behavior Invariants

1. A fresh clone exposes clear commands for install, typecheck, test, build, and formatting/linting once dependencies are installed.
2. The workspace separates runtime surfaces by ownership:
   - `packages/protocol`
   - `apps/daemon`
   - `packages/cli`
   - `apps/web`
   - `skills/agent-blackboard`
3. No package should depend on the web renderer to understand the core platform model.
4. OpenUI-specific code belongs behind a web or renderer adapter boundary, not inside the protocol kernel.
5. Temporary outputs, screenshots, generated reports, and scratch files go under `.out/`.
6. The scaffold must leave room for future remote mode without adding remote support in the MVP.

## States And Edge Cases

- If dependencies are not installed, commands should fail with standard package-manager guidance rather than custom shell wrappers.
- If a package is still empty, its placeholder command should be explicit and easy to replace.
- If the chosen package manager changes later, update this spec and the README in the same change.
- If a validation command is intentionally unavailable, record the reason in the implementation handoff.

## Open Questions

- Should the package manager be `pnpm` by default? This spec assumes `pnpm` unless implementation finds a stronger reason to choose otherwise.
- Should the first scaffold include GitHub Actions, or wait until protocol and daemon tests exist?
- Which Node.js version should be pinned for local development?
