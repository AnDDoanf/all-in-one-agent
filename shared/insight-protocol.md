# Shared Insight Protocol

Every skill MUST follow this protocol.

```
       ┌────────────────────────────────────────────────────────┐
       │                 1. Resolve Repository                  │
       └───────────────────────────┬────────────────────────────┘
                                   │
       ┌───────────────────────────▼────────────────────────────┐
       │                 2. Read Insight First                  │
       └───────────────────────────┬────────────────────────────┘
                                   │
       ┌───────────────────────────▼────────────────────────────┐
       │                  3. Check Freshness                    │
       └───────────────────────────┬────────────────────────────┘
                                   │
                       Fresh? ─────┴───── Missing/Stale?
                      /                                 \
          ┌──────────▼──────────┐             ┌──────────▼──────────┐
          │ Re-use Cached Data  │             │ 4. Targeted Explore │
          └──────────┬──────────┘             └──────────┬──────────┘
                      \                                 /
       ┌───────────────▼───────────────────────────────▼────────┐
       │                   5. Execute Skill                     │
       └───────────────────────────┬────────────────────────────┘
                                   │
       ┌───────────────────────────▼────────────────────────────┐
       │                6. Synchronize Insight                  │
       └───────────────────────────┬────────────────────────────┘
                                   │
       ┌───────────────────────────▼────────────────────────────┐
       │                       7. Report                        │
       └────────────────────────────────────────────────────────┘
```

---

## 1. Resolve Repository
- Identify the active target source repository (e.g. `metronome`, `anhoc`, `anchi`).
- Resolve its entry in [`insight/registry.json`](../../insight/registry.json).
- Never confuse knowledge or mix state between repositories.

## 2. Read Insight First
- Read `insight/<repo>/INDEX.md` as the table of contents.
- Load relevant architecture specifications, module boundaries, coding-style conventions, data schemas, and API contracts.
- Load **only documents relevant to the current task** to optimize token usage.

## 3. Check Freshness
- Read the repository manifest: `insight/<repo>/manifest.json`.
- Check affected source hashes, git revisions, and timestamps against current source files.
- Distinguish the confidence levels of the insight:
  - **Verified**: Matches current source commit/hash.
  - **Stale**: Source files have changed since the last insight update.
  - **Unknown / Missing**: No documented insight yet exists.

## 4. Explore When Necessary
- Prefer targeted source analysis rather than full-codebase exploration.
- If insight is verified and sufficient, **skip scanning source code**.
- If insight is missing or stale, inspect only affected source files and modules.
- Reuse existing AST tools, dependency graphs, and search utilities.

## 5. Execute Skill
- Follow the skill's specialized workflow as documented in `Agent/skills/<skill-name>/SKILL.md`.
- Strictly adhere to repository-specific conventions documented in `insight/<repo>/coding-style/`.
- Verify critical details against active source code before executing modifications.

## 6. Synchronize Insight
- Update only impacted knowledge artifacts in `insight/<repo>/`.
- Include concrete source references (`file:///path/to/file#L10-L25`) and current git revision data.
- Update `insight/<repo>/manifest.json` with new file hashes and update timestamps.
- **Preserve manually authored documentation**; never overwrite human notes without verification.
- Validate documentation format and links before finalizing.
- Never silently overwrite another agent's recent edits.

## 7. Report
Always provide a concise final report containing:
- **Work Completed**: Summary of code or analysis performed.
- **Source Files Affected**: List of changed source files.
- **Insight Artifacts Updated**: List of documentation files refreshed in `insight/<repo>/`.
- **Stale or Unverified Knowledge**: Any gaps identified for future exploration.
