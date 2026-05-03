---
language: en-US
audience: mixed
doc_type: overview
---

# agent-blackboard

Local-first Agentic UI blackboard for Codex threads.

`agent-blackboard` is an experimental display layer for Codex and other agents. The first version is focused on local task progress visualization: one shared daemon, multiple Codex threads, per-thread runs, OpenUI-generated pages, artifacts, and structured human input surfaces.

## Initial Direction

- Local daemon shared by Codex threads.
- Per-workspace, per-thread, per-run isolation.
- OpenUI page surfaces for agent-generated and continuously patched pages.
- Append-only events for progress, lifecycle, and evidence.
- Artifact references for generated files, screenshots, reports, and links.
- User actions routed back to the owning run.

## Status

Early project notes live in the companion Obsidian vault. Implementation has not started yet.

## Governance

This repository uses Code & Order governance. Start with `AGENTS.md`, then follow the relevant workflow under `docs/governance/`.

Project work is spec-first by default. Tiny mechanical edits can be direct when they do not affect behavior, contracts, durable docs, or governance.
