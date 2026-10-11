---
name: migration-assistant
description: Guide and execute codebase migrations across framework versions, language editions, runtime environments, or major libraries.
---

# Migration Assistant

## Required First Step

Read `../shared/insight-protocol.md` and follow it throughout this task.

## Purpose & When to Use

Use this skill when upgrading major framework versions (e.g. Next.js App Router, Vue 2 to 3, Python 3.8 to 3.12), migrating build tools (Webpack to Vite), or swapping major dependencies.

## Workflow

1. **Resolve Repository**: Check target repository in `insight/registry.json`.
2. **Read Architecture & Contracts**:
   - Check `insight/<repo>/architecture/system-overview.md` and `dependencies.md`.
3. **Formulate Phased Migration Plan**:
   - Phase 1: Dependency updates & configuration alignment.
   - Phase 2: Codemod execution or syntax transformations.
   - Phase 3: Breaking change deprecation replacements.
   - Phase 4: Integration testing and validation.
4. **Execute Phased Changes**:
   - Apply transformations incrementally on isolated branches or modules.
   - Run test suite after each phase.
5. **Document Migration Decisions**:
   - Create `insight/<repo>/decisions/migration-<name>.md` detailing motivation, breaking changes, and rollback instructions.
6. **Synchronize Insight**:
   - Update `insight/<repo>/architecture/` to reflect new version baselines.
7. **Report**: Summarize migration progress and verified test outcomes.

## Constraints

- Never perform all migration phases in a single unverified commit.
- Maintain fallback compatibility during ongoing multi-step migrations.
