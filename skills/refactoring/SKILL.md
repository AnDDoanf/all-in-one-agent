---
name: refactoring
description: Restructure and simplify existing code without altering external behavior, enforcing decoupling and modularity.
---

# Refactoring

## Required First Step

Read `../shared/insight-protocol.md` and follow it throughout this task.

## Purpose & When to Use

Use this skill when cleaning code debt, extracting reusable services, decoupling tangled dependencies, or improving maintainability.

## Workflow

1. **Resolve Repository**: Check target repository in `insight/registry.json`.
2. **Read Insight**:
   - Check `insight/<repo>/modules/` to understand current module boundaries.
   - Check `insight/<repo>/architecture/system-overview.md`.
3. **Establish Safety Harness**:
   - Verify that test suite passes *before* making changes.
   - If test coverage is insufficient, invoke `test-generator` first.
4. **Execute Refactoring Steps**:
   - Perform small, incremental transformations (e.g. Extract Function, Move Method, Replace Conditional with Polymorphism).
   - Keep behavior bit-for-bit identical from the perspective of callers.
5. **Verify**:
   - Run unit and integration tests after each incremental change.
   - Ensure linter and type-checker pass cleanly.
6. **Synchronize Insight**:
   - Update `insight/<repo>/modules/` and `insight/<repo>/architecture/` if module paths or interfaces were relocated.
7. **Report**: Summarize refactored units and verified invariants.

## Constraints

- Never combine behavioral changes (feature additions or bug fixes) with refactoring in a single step.
- Ensure all public exports maintain backwards compatibility unless an intentional breaking change is requested.
