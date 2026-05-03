---
language: en-US
audience: agent
doc_type: router
---

# Specs

Use `docs/governance/spec-first-delivery.md` for the fixed coordinator -> worker -> acceptance flow, `docs/governance/compact-specs.md` for bug fix and small tweak specs, `docs/governance/spec-production.md` for creating specs, `docs/governance/spec-workflow.md` for the spec lifecycle, `docs/governance/spec-id-policy.md` for id format, `docs/governance/spec-execution-status.md` for execution status, and `docs/governance/multi-agent-spec-flow.md` for parallel implementation.

Each substantial spec should live under:

```text
specs/<source>-<id>-<short-slug>/
  PRODUCT.md
  TECH.md
  STATUS.md
  workstreams/
    01-implementation.md
```

## Current Spec Map

| Spec | Purpose | Status |
|---|---|---|
| `rfc-0001-initial-governance` | Code & Order initialization | validated |
| `rfc-0002-mvp-scope-and-repo-scaffold` | MVP boundary, repository scaffold, baseline commands | ready |
| `rfc-0003-protocol-and-storage` | Core data model, event protocol, SQLite persistence | ready |
| `rfc-0004-local-daemon-and-cli` | Local daemon API, SSE, and `displayctl` | ready |
| `rfc-0005-web-openui-and-skill` | Web UI, OpenUI page renderer, component catalog, Codex skill | draft |

Implementation should start with `rfc-0002`, then `rfc-0003`, then `rfc-0004`. `rfc-0005` remains draft until OpenUI package integration is inspected during or after the scaffold work.
