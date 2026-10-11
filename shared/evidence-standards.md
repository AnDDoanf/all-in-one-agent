# Evidence Standards

All agents contributing to or reading from `insight/` must adhere to these evidence standards.

---

## 1. Grounding Principles

1. **No Hallucinated Contracts**: Never document an API endpoint, data model, or architectural pattern based on assumptions. Every claim must have verifiable evidence in the source repository.
2. **Explicit Citations**: When updating insight documentation, link directly to source files and line ranges:
   - Format: `[SymbolName](file:///path/to/source/file.ext#L10-L45)`
3. **Evidence Tiers**:

| Tier | Status | Requirement |
|---|---|---|
| **Tier 1: AST / Compiler Verified** | `verified` | Confirmed by parser/AST tooling (e.g. ts-morph, OpenAPI spec, test runner, compiler type check). |
| **Tier 2: Static Heuristic** | `heuristic` | Confirmed by regex/grep search or config analysis. |
| **Tier 3: Inferred / Observation** | `inferred` | Deduced from runtime logs or surrounding code context. Must be flagged as `[Inferred]`. |
| **Tier 4: Stale** | `stale` | Documented earlier, but the referenced source file has since changed. |

---

## 2. Citation Requirements in Insight Documents

Every insight document must include an **Evidence Block** at the top or bottom:

```markdown
<!-- EVIDENCE_BLOCK
source_repo: metronome
source_commit: a3f1b4c
verified_files:
  - path: src/core/timer.ts
    hash: 8f9a2e4...
    lines: 12-88
  - path: src/api/routes.ts
    hash: 5b1d9c0...
    lines: 104-140
tier: verified
verified_by: agent:claude-code
timestamp: 2026-10-11T23:30:00Z
-->
```

---

## 3. Discrepancy Resolution

If an insight document contradicts the source code:
1. **Source code is always the source of truth.**
2. Mark the insight document as `stale` or update it immediately to reflect reality.
3. Do not silently propagate incorrect architectural assertions into downstream tasks.
