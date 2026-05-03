---
language: en-US
audience: agent
doc_type: spec
---

# Web OpenUI And Skill Tech Spec

Product spec: `./PRODUCT.md`

## Context

This spec depends on `rfc-0002-mvp-scope-and-repo-scaffold`, `rfc-0003-protocol-and-storage`, and `rfc-0004-local-daemon-and-cli`.

The project notes recommend Vite + React for the web UI, OpenUI as the first generated page surface, and a Codex skill that uses `displayctl`. The exact OpenUI package API must be inspected before implementation, so this spec remains `draft`.

## Change Gate

- Problem: users need a local visual surface for Codex progress, generated pages, artifacts, and decisions.
- Existing path considered: use fixed dashboard blocks only.
- Why existing path is insufficient: the first product question is whether agents can generate and continuously modify pages.
- Smallest new surface: web shell, OpenUI renderer adapter, small custom component catalog, skill guidance.
- What will be deleted or replaced: any temporary demo renderer or sample component that does not become part of the catalog.
- Owner: web/OpenUI/skill workstream owners.
- Validation: browser smoke checks, renderer error tests, skill example dry run.
- Temporary or permanent: web shell and skill are permanent; experimental components are temporary until accepted into catalog.
- Removal condition: replace experimental components when task-page dogfood shows they are unstable or unnecessary.

## Proposed Changes

- Add `apps/web` with a local UI shell.
- Add an OpenUI renderer adapter for `openui-page` surfaces.
- Add first custom components:
  - `RunHeader`
  - `StatusStrip`
  - `StepList`
  - `Timeline`
  - `ContextPanel`
  - `FileChangeList`
  - `ArtifactGrid`
  - `DecisionPanel`
- Add action UI for approve/reject, choose, comment, and simple forms if supported by protocol.
- Add `skills/agent-blackboard/SKILL.md` and examples that teach:
  - starting or resolving the daemon;
  - beginning a run;
  - creating and patching an overview page;
  - reporting status and artifacts;
  - requesting and waiting for actions;
  - completing or clearing a run.

## Workstream Split

- `01-web-shell`: navigation, active runs, selected run layout.
- `02-openui-renderer`: OpenUI adapter, surface diagnostics, patch display.
- `03-component-catalog`: Codex task components and prompt/reference generation.
- `04-actions-ui`: user input UI and action queue display.
- `05-codex-skill`: skill docs, examples, and guardrails.
- `06-visual-validation`: screenshots and browser smoke checks.

## Testing And Validation

- Web build and typecheck.
- Browser smoke check showing at least one run with an OpenUI page surface.
- Renderer failure state test.
- Action submission round-trip test.
- Skill example dry run that creates or patches a page through `displayctl`.
- Visual evidence for desktop and narrow viewport states.

## Risks And Follow-Ups

- OpenUI APIs may change. Keep the adapter isolated.
- The custom catalog can become too large. Add components only when they reduce prompt ambiguity.
- Skill guidance can become noisy. Keep `SKILL.md` short and move detailed examples to references.
- Sandbox app support, A2UI compatibility, and remote mode should be separate future specs.
