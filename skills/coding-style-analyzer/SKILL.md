---
name: coding-style-analyzer
description: Analyze, document, and verify repository-specific coding conventions, idioms, naming rules, error handling, and lint rules.
---

# Coding Style Analyzer

## Required First Step

Read `../shared/insight-protocol.md` and follow it throughout this task.

## Purpose & When to Use

Use this skill when:
- Establishing initial coding style documentation for a repository.
- Resolving style ambiguities or linting inconsistencies across the team.
- Preparing to implement code in a repository with unfamiliar stylistic conventions.

## Workflow

1. **Resolve Repository**: Check target repository in `insight/registry.json`.
2. **Read Existing Style Insight**: Load `insight/<repo>/coding-style/conventions.md`.
3. **Inspect Configuration**:
   - Check `.eslintrc*`, `biome.json`, `prettierrc`, `ruff.toml`, `flake8`, or IDE settings.
4. **Empirical Sampling**:
   - Sample at least 3-5 existing idiomatic source files across the codebase.
   - Analyze:
     - Naming conventions (files, variables, interfaces, components).
     - Error handling patterns (custom error classes, Result types, try/catch vs monadic).
     - State management / mutability idioms.
     - Asynchronous paradigms (async/await, Observables, promises).
5. **Document Verified Conventions**:
   - Write or update `insight/<repo>/coding-style/conventions.md`.
   - Provide concrete code examples extracted from source files with exact line links.
6. **Synchronize Insight**:
   - Update `insight/<repo>/manifest.json` with citations.
7. **Report**: Summarize documented patterns and style guidelines.

## Constraints

- Never invent style guidelines based on external habits; document what is actually practiced.
- Require at least 3 occurrences in the codebase to designate a pattern as a convention.
- Distinguish mandatory rules (enforced by linter) from idiomatic recommendations.
