---
language: en-US
audience: mixed
doc_type: spec
---

# Web OpenUI And Skill Product Spec

## Summary

Build the user-facing local web UI, OpenUI page rendering surface, first Codex task-visualization component catalog, and `agent-blackboard` Codex skill guidance.

This spec stays draft until OpenUI integration details are inspected in the scaffolded repo.

## Goals

- Show workspaces, threads, active runs, and run details in a local web UI.
- Render `openui-page` surfaces produced and patched by agents.
- Surface renderer/parser errors so agents can repair broken page output.
- Provide a small custom component catalog for Codex task progress pages.
- Provide a concise Codex skill that teaches agents when and how to write to the blackboard.
- Support simple user input actions routed back to the owning run.

## Non-Goals

- Do not support arbitrary sandbox apps in v1.
- Do not support remote/multi-machine display.
- Do not replace observability tools such as Langfuse.
- Do not make chat the primary UI.
- Do not require agents to hand-write React.

## Behavior Invariants

1. The web UI can show all active runs and drill into a selected run.
2. A selected run displays its current `openui-page` surface and relevant metadata.
3. Renderer errors are visible and persisted as surface diagnostics.
4. User actions include enough run and surface context for the daemon or CLI to return them to the owning agent.
5. The custom component catalog stays small and task-specific in the MVP.
6. The skill uses `displayctl` examples instead of directly describing daemon internals.
7. The skill teaches material-update cadence: begin, status changes, page creation, page patch, artifact add, input request, completion.

## States And Edge Cases

- No daemon reachable.
- No workspaces or runs yet.
- OpenUI source cannot parse or render.
- A surface update arrives while the user is viewing the page.
- User submits an action after the run is completed.
- Artifact path or URL cannot be opened.
- Skill is invoked before `displayctl` is available.

## Open Questions

- Which exact OpenUI package and renderer API should be used?
- What is the smallest custom component catalog that still gives Codex stable output?
- Should page patch validation happen in the CLI, daemon, web renderer, or all three?
- Should the web UI include a raw event inspector in the MVP?
