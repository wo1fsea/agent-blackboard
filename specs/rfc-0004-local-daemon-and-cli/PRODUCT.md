---
language: en-US
audience: mixed
doc_type: spec
---

# Local Daemon And CLI Product Spec

## Summary

Implement the local daemon and `displayctl` command that Codex threads use to create runs, publish progress, update surfaces, attach artifacts, and complete or clear their own data.

## Goals

- Provide an idempotent `displayctl up` flow for starting or discovering the local daemon.
- Provide local HTTP APIs for run, surface, event, artifact, and action state.
- Provide SSE updates so the web UI can refresh without polling.
- Provide a small CLI surface suitable for Codex skill examples.
- Keep all daemon access localhost-only in the MVP.

## Non-Goals

- Do not implement the web UI shell.
- Do not render OpenUI pages.
- Do not implement remote authentication or cross-machine routing.
- Do not expose a public cloud API.
- Do not require daemon-to-Codex callbacks; use polling or wait commands for actions.

## Behavior Invariants

1. `displayctl up` is safe to run repeatedly and returns the daemon URL and run-state location.
2. The daemon writes state under the configured local blackboard home, defaulting to `~/.codex/agent-blackboard/`.
3. API writes validate against `packages/protocol` schemas.
4. `displayctl begin` creates a run scoped to the current workspace and thread identity.
5. `displayctl status`, `displayctl event`, and `displayctl page` produce durable events or surface updates.
6. `displayctl complete` marks only the current run complete.
7. `displayctl clear`, `archive`, and `delete` require explicit scope.
8. SSE emits enough information for the web UI to update active run lists and selected run surfaces.

## States And Edge Cases

- Daemon already running.
- Port unavailable.
- Stale `daemon.json`.
- Missing thread id.
- Invalid payload from CLI.
- Database locked or unavailable.
- Action wait times out.
- User clears a run while SSE clients are connected.

## Open Questions

- Should `displayctl up` automatically open the browser, or only print the URL?
- Should the daemon choose a fixed port first or always allocate an available port?
- What is the initial thread id fallback when Codex does not expose a session id?
