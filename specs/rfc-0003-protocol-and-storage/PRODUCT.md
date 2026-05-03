---
language: en-US
audience: mixed
doc_type: spec
---

# Protocol And Storage Product Spec

## Summary

Define the minimal `agent-blackboard` protocol and local persistence model so Codex threads can create runs, publish surfaces and events, attach artifacts, and receive user actions without relying on chat history.

## Goals

- Define stable entities: `workspace`, `thread`, `run`, `surface`, `event`, `artifact`, and `action`.
- Validate protocol payloads before they reach storage.
- Store append-only events and current surface snapshots in SQLite.
- Support local multi-thread isolation through scoped identifiers.
- Support lifecycle operations for completing, archiving, clearing, and deleting run-owned data.
- Keep protocol and storage independent of OpenUI rendering.

## Non-Goals

- Do not implement HTTP routes or CLI commands.
- Do not render surfaces in a browser.
- Do not support remote auth or multi-machine routing.
- Do not add arbitrary sandbox app payloads.
- Do not decide final OpenUI component catalog.

## Behavior Invariants

1. Every write is scoped by workspace and run; thread scope is required for Codex-owned runs.
2. Event records are append-only and preserve enough metadata to reconstruct progress history.
3. Surface records hold the current snapshot plus monotonically increasing revisions.
4. Surface updates with stale base revisions are rejected or explicitly recorded as conflicts.
5. Artifacts are stored as references with type, path or URL, and ownership metadata; storage must not silently copy arbitrary files.
6. Actions are queued against the owning run and can be marked pending, consumed, cancelled, or expired.
7. Clear, archive, and delete operations cannot affect another thread or workspace unless explicitly scoped to do so.
8. Protocol schemas use versioned message shapes so future adapters can map AG-UI, A2UI, or other formats later.

## States And Edge Cases

- Missing workspace or thread identity.
- Duplicate begin-run requests.
- Concurrent surface updates.
- SQLite database missing, locked, or migrated from an older schema.
- Artifact path outside allowed local roots.
- User action arrives after a run is completed.
- Clear/delete is requested while the web UI is reading the run.

## Open Questions

- Should artifact references support both absolute paths and copied files in the MVP?
- Should action expiration be time-based, run-completion-based, or explicit only?
- What exact thread id source is available in Codex Desktop and Codex CLI?
