# Update Policy

This document defines how agents read and safely update the shared knowledge base (`insight/`).

---

## 1. Concurrency and Multi-Agent Safety

Because multiple agents (Codex, Claude Code, Gemini CLI) may access the same `insight/` directory:

1. **Targeted Updates**: Modify only the specific files directly impacted by your task. Never regenerate the entire `insight/` tree during an incremental task.
2. **Atomic Writes**: Always write files completely or use atomic file swap mechanisms to prevent partially written markdown.
3. **Preserve Human Annotations**: If a section is tagged with `<!-- USER_EDIT_START -->` and `<!-- USER_EDIT_END -->`, agents MUST NOT overwrite or alter it without explicit user consent.
4. **Manifest Synchronization**: Whenever any `.md` file inside `insight/<repo>/` is updated:
   - Recalculate its SHA-256 hash.
   - Update `insight/<repo>/manifest.json` with the updated artifact entry, last updated timestamp, and authoring agent identifier (`agent:codex`, `agent:claude`, `agent:gemini`).

---

## 2. When to Update Insight

| Skill Executed | When to Update Insight | Target Artifacts |
|---|---|---|
| `codebase-explorer` | First repository bootstrap or major architectural changes. | `INDEX.md`, `SPEC.md`, `architecture/*`, `modules/*` |
| `coding-style-analyzer` | Lint config updates, new patterns discovered with >3 examples. | `coding-style/*` |
| `feature-implementation` | New public endpoints, modified schemas, new components. | `modules/*`, `api/*`, `flows/*` |
| `code-review` | Systematic flaws discovered, newly verified conventions. | `decisions/*`, `coding-style/*` |
| `test-generator` | New test suites, coverage contracts, integration fixtures. | `modules/tests.md` |
| `debugging` | Root causes uncovered that expose subtle system quirks. | `decisions/*`, `architecture/gotchas.md` |
| `frontend-development` | Changed component tree, design tokens, route changes. | `architecture/frontend.md`, `flows/*` |
| `api-development` | Modified REST/GraphQL endpoints, request/response models. | `api/*` |
| `database-migration` | New tables, altered columns, foreign keys, seeds. | `database/*` |
| `refactoring` | Altered package boundaries, extracted services, renamed symbols. | `architecture/*`, `modules/*` |
| `security-audit` | Discovered threat models, updated auth flows, sanitization rules. | `architecture/security.md` |
| `performance-optimization` | Added caches, indexing strategies, benchmark results. | `architecture/performance.md` |
| `pr-preparation` | Generating release impact notes and changelog summaries. | `decisions/*`, `INDEX.md` |
| `dependency-management` | Added, upgraded, or removed packages and lockfiles. | `manifest.json`, `architecture/dependencies.md` |
| `documentation` | General maintenance, diagrams, synchronization passes. | All relevant `insight/` docs |
| `migration-assistant` | Migration milestones, breaking changes, deprecation paths. | `decisions/migrations.md` |

---

## 3. Conflict Prevention

If an agent notices that `manifest.json` indicates an update from another agent less than 5 minutes ago:
1. Re-read the changed artifact before applying updates.
2. Perform a line-level diff rather than a blind file overwrite.
3. Keep both verified assertions if non-contradictory.
