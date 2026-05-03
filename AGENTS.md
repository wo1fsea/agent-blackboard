# AGENTS.md

This repository is the implementation home for `agent-blackboard`.

## Current Intent

Build a local-first Agentic UI blackboard for Codex threads:

- shared local daemon;
- per-workspace and per-thread runs;
- OpenUI-generated and continuously patched page surfaces;
- progress, context, artifacts, and data visualization;
- structured human input routed back to the owning run;
- a Codex skill that teaches agents how to use the platform.

## Early Guardrails

- Keep the platform kernel independent of OpenUI. OpenUI is a page surface, not the lifecycle model.
- Prefer a small protocol around `workspace`, `thread`, `run`, `surface`, `event`, `artifact`, and `action`.
- Start local-first before remote/multi-machine support.
- Do not add arbitrary sandboxed frontend apps in the MVP.
- Keep the agent-facing skill concise and example-driven.

