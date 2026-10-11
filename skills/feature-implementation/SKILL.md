---
name: feature-implementation
description: Implement features using existing repository architecture, documented patterns, and coding conventions.
---

# Feature Implementation

## Required First Step

Read `../shared/insight-protocol.md` and follow it throughout this task.

## Purpose & When to Use

Use this skill when developing new features, user stories, domain logic, or extending existing functionality.

## Workflow

1. **Resolve Target Repository**: Identify target repository in `insight/registry.json`.
2. **Read Insight Index**: Read `insight/<repo>/INDEX.md` and `SPEC.md`.
3. **Identify Affected Modules**: Read relevant files in `insight/<repo>/modules/`.
4. **Load Coding Style**: Load `insight/<repo>/coding-style/conventions.md`.
5. **Load Contracts & Schemas**: Load associated API contracts (`insight/<repo>/api/`) and database models (`insight/<repo>/database/`).
6. **Verify in Source Code**: Verify targeted source files before touching them.
7. **Implement Feature**:
   - Adhere strictly to existing architectural patterns and naming rules.
   - Reuse existing utilities, abstractions, and validation libraries.
8. **Run Tests & Linters**: Execute repository unit and integration tests.
9. **Identify Changed Architecture**: Note any new public exports, endpoints, or data models.
10. **Synchronize Insight**: Update impacted documentation artifacts in `insight/<repo>/`.
11. **Report**: Summarize implementation details, tests run, and insight updates.

## Constraints

- Never invent repository conventions or bypass existing abstraction layers.
- Avoid unnecessary full-repository scans.
- Do not treat stale documentation as authoritative; verify against source.
- Do not modify unrelated modules.
