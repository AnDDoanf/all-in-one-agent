---
name: codebase-explorer
description: Explore, map, and bootstrap repository architecture, module boundaries, entry points, and high-level structure.
---

# Codebase Explorer

## Required First Step

Read `../shared/insight-protocol.md` and follow it throughout this task.

## Purpose & When to Use

Use this skill when:
- Bootstrapping insight for a new or undocumented repository.
- Investigating unfamiliar subsystems or major architectural reorganizations.
- Re-verifying stale high-level architecture maps.

## Workflow

1. **Resolve Repository**: Identify target repository in `insight/registry.json`.
2. **Read Insight**: Inspect `insight/<repo>/INDEX.md` and `insight/<repo>/SPEC.md`. Check freshness in `manifest.json`.
3. **Targeted Scan**:
   - Inspect root config files (`package.json`, `tsconfig.json`, `Cargo.toml`, `pyproject.toml`, etc.).
   - Locate primary entry points (`src/index.*`, `src/main.*`, `cmd/`, `app/`).
   - Run `scripts/scan-structure.ts` or inspect top-level module directories.
4. **Identify Module Boundaries**:
   - Map module dependencies and interfaces.
   - Consult `references/architecture-patterns.md` for standard layering conventions.
5. **Document Architecture**:
   - Draft or update `insight/<repo>/architecture/system-overview.md`.
   - Update `insight/<repo>/modules/index.md`.
   - Generate Mermaid architecture diagrams in `insight/<repo>/flows/`.
6. **Synchronize Insight**:
   - Update `insight/<repo>/manifest.json` with verified file citations.
   - Update `insight/<repo>/INDEX.md` table of contents.
7. **Report**: Summarize discovered modules, entry points, and updated insight files.

## Constraints

- Do not perform unbounded file reads; focus on boundaries, exports, and directory layout.
- Preserve manual human annotations in existing insight documents.
- Always include explicit file references for discovered modules.
