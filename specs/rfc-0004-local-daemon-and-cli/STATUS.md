---
spec_id: rfc-0004-local-daemon-and-cli
language: en-US
audience: agent
doc_type: spec
status: ready
implementation: not_started
validation: not_started
coordinator:
updated: 2026-05-04
---

# Status

## Summary

Ready after scaffold and protocol work. This spec provides the local daemon and `displayctl` surface that Codex threads will use.

## Workstreams

| ID | Scope | Status | Owner | Branch / PR | Depends on | Updated |
|---|---|---|---|---|---|---|
| 01 | Daemon lifecycle | ready | unassigned | | rfc-0002, rfc-0003 | 2026-05-04 |
| 02 | Run and surface API | ready | unassigned | | 01 | 2026-05-04 |
| 03 | SSE stream | ready | unassigned | | 02 | 2026-05-04 |
| 04 | displayctl CLI | ready | unassigned | | 01, 02 | 2026-05-04 |
| 05 | Validation | ready | unassigned | | 01, 02, 03, 04 | 2026-05-04 |

## Activity Log

- 2026-05-04: spec created from MVP architecture notes.

## Main Session Acceptance

- Accepted by:
- Diff reviewed:
- Validation run:
- Residual risk:
