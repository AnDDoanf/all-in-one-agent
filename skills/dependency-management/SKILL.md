---
name: dependency-management
description: Audit, upgrade, and reconcile external dependencies, lockfiles, and package licenses across workspace repositories.
---

# Dependency Management

## Required First Step

Read `../shared/insight-protocol.md` and follow it throughout this task.

## Purpose & When to Use

Use this skill when adding new packages, upgrading libraries, fixing vulnerability advisories (`npm audit`, `pip-audit`), or reconciling lockfile conflicts.

## Workflow

1. **Resolve Repository**: Look up target repository in `insight/registry.json`.
2. **Read Dependency Insight**:
   - Check `insight/<repo>/architecture/dependencies.md` for approved libraries and lockfile strategy.
3. **Inspect Manifest**:
   - Inspect `package.json`, `pnpm-lock.yaml`, `requirements.txt`, `Cargo.lock`, etc.
4. **Evaluate Proposed Packages**:
   - Verify bundle weight, license compliance (e.g. MIT, Apache 2.0 vs GPL restrictions), and maintenance status.
   - Prefer existing packages in the workspace before introducing a new library.
5. **Execute Update**:
   - Run package manager command (`pnpm add`, `npm update`, etc.).
   - Regenerate lockfile cleanly.
6. **Verify Build & Tests**:
   - Run full build and test suite to check for breaking changes or peer dependency warnings.
7. **Synchronize Insight**:
   - Update `insight/<repo>/architecture/dependencies.md` with new dependency inventory.
8. **Report**: Summarize added/updated packages and verification status.

## Constraints

- Never commit package manifests without the corresponding lockfile.
- Do not introduce redundant utility libraries (e.g. adding `lodash` if already using modern ES6+ or `radash`).
