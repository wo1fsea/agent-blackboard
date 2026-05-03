---
language: en-US
audience: agent
doc_type: spec
---

# MVP Scope And Repo Scaffold Tech Spec

Product spec: `./PRODUCT.md`

## Context

The repository currently has governance files, initial project notes, and no implementation scaffold. The project direction from `AGENTS.md` is local-first: a shared daemon, per-workspace/thread runs, OpenUI page surfaces, progress/context/artifact display, user actions, and a Codex skill.

The first implementation change should create stable ownership boundaries before any runtime behavior lands.

## Change Gate

- Problem: future work needs multiple packages and apps, and adding them opportunistically would blur ownership.
- Existing path considered: keep files at repo root until the runtime grows.
- Why existing path is insufficient: protocol, daemon, CLI, web, and skill have different dependencies and validation paths.
- Smallest new surface: workspace layout, package scripts, package boundaries, baseline config files.
- What will be deleted or replaced: any temporary placeholder scripts added only to bootstrap the scaffold should be removed when real commands exist.
- Owner: `agent-blackboard` maintainers.
- Validation: install, typecheck, test, build, and package script discovery.
- Temporary or permanent: permanent layout; placeholder commands are temporary.
- Removal condition: placeholder commands are removed when real package implementations land.

## Proposed Changes

- Add workspace package metadata.
- Add baseline TypeScript and formatting/linting config only where it supports immediate validation.
- Create empty or minimal package/app directories:
  - `packages/protocol`
  - `apps/daemon`
  - `packages/cli`
  - `apps/web`
  - `skills/agent-blackboard`
- Add README guidance for install and validation once scripts exist.
- Keep package dependencies minimal until the owning implementation spec needs them.

## Workstream Split

- `01-workspace-tooling`: package manager, root scripts, shared config.
- `02-package-boundaries`: directories, package metadata, dependency direction notes.
- `03-baseline-validation`: placeholder or real validation commands and first smoke checks.
- `04-docs`: README updates and implementation handoff notes.

## Testing And Validation

- Package manager install command.
- Root script listing.
- Typecheck command, even if initially only checks config.
- Test command, even if initially limited to no-op or placeholder package tests.
- Build command, scoped to packages/apps that exist.
- Code & Order audit should still report expected customized files only.

## Risks And Follow-Ups

- Choosing dependencies too early can create churn. Add dependencies only when a workstream needs them.
- Placeholder commands can hide missing validation. Mark them clearly and replace them in the first runtime spec that needs them.
- CI is intentionally deferred unless implementation decides local commands are stable enough.
