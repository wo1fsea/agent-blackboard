---
spec_id: rfc-0005-web-openui-and-skill
language: en-US
audience: agent
doc_type: spec
status: draft
implementation: not_started
validation: not_started
coordinator:
updated: 2026-05-04
---

# Status

## Summary

Draft. The product direction is clear, but implementation should not start until OpenUI package integration is inspected in the scaffolded repo.

## Workstreams

| ID | Scope | Status | Owner | Branch / PR | Depends on | Updated |
|---|---|---|---|---|---|---|
| 01 | Web shell | ready | unassigned | | rfc-0002, rfc-0003, rfc-0004 | 2026-05-04 |
| 02 | OpenUI renderer | ready | unassigned | | 01 | 2026-05-04 |
| 03 | Component catalog | ready | unassigned | | 02 | 2026-05-04 |
| 04 | Actions UI | ready | unassigned | | rfc-0003, rfc-0004, 01 | 2026-05-04 |
| 05 | Codex skill | ready | unassigned | | rfc-0004, 02, 03, 04 | 2026-05-04 |
| 06 | Visual validation | ready | unassigned | | 01, 02, 03, 04, 05 | 2026-05-04 |

## Activity Log

- 2026-05-04: draft spec created from project notes.

## Draft Exit Criteria

- OpenUI package and renderer API are inspected in the scaffolded workspace.
- The first component catalog shape is confirmed.
- The action model from `rfc-0003` and `rfc-0004` is stable enough for UI work.

## Main Session Acceptance

- Accepted by:
- Diff reviewed:
- Validation run:
- Residual risk:
