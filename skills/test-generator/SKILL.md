---
name: test-generator
description: Generate unit, integration, and contract tests aligned with repository testing frameworks, fixtures, and coverage standards.
---

# Test Generator

## Required First Step

Read `../shared/insight-protocol.md` and follow it throughout this task.

## Purpose & When to Use

Use this skill when:
- Creating tests for newly implemented or untested code.
- Increasing test coverage for critical domain logic or API endpoints.
- Generating regression tests for fixed bugs.

## Workflow

1. **Resolve Repository**: Identify repository in `insight/registry.json`.
2. **Read Testing Patterns**:
   - Check `insight/<repo>/coding-style/conventions.md` (testing section).
   - Check `insight/<repo>/modules/` to locate test framework in use (e.g. Vitest, Jest, Pytest, Go test).
3. **Inspect Existing Test Fixtures**:
   - Locate adjacent test files (`*.spec.ts`, `*.test.ts`, `tests/`).
   - Identify mocking strategies, mock data generators, and test database runners.
4. **Targeted Analysis**: Inspect only the file(s) or functions under test.
5. **Generate Tests**:
   - Write tests following existing naming (`describe`, `it`, `test`).
   - Cover happy paths, boundary conditions, and error branches.
   - Use existing mock factories and helpers.
6. **Execute & Verify**:
   - Run the newly created test suite via project test runner.
   - Ensure all tests pass.
7. **Synchronize Insight**:
   - Update testing coverage notes in `insight/<repo>/modules/`.
8. **Report**: Report tests created and execution results.

## Constraints

- Never use mocks when real contracts are expected by repository conventions.
- Do not write brittle tests coupled to private implementation details.
