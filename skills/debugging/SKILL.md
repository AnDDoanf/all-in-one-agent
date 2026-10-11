---
name: debugging
description: Investigate, reproduce, and resolve defects using documented data flows, error models, and targeted source inspection.
---

# Debugging

## Required First Step

Read `../shared/insight-protocol.md` and follow it throughout this task.

## Purpose & When to Use

Use this skill when:
- Investigating runtime exceptions, failing tests, or incorrect output.
- Tracing data corruption across asynchronous pipelines or service boundaries.

## Workflow

1. **Resolve Repository**: Look up target repository in `insight/registry.json`.
2. **Read Flow & Architecture Insight**:
   - Check `insight/<repo>/flows/` to trace expected sequence diagrams.
   - Check `insight/<repo>/architecture/gotchas.md` (if existing) for known pitfalls.
3. **Reproduce Defect**:
   - Write a minimal failing test or reproduction script.
4. **Isolate Root Cause**:
   - Trace variables and execution path from entry point to point of failure.
   - Check edge case assumptions and type coercions.
5. **Implement Fix**:
   - Make minimal, targeted modifications.
   - Preserve existing architectural patterns.
6. **Verify Fix**:
   - Run the reproduction test and the broader test suite.
7. **Synchronize Insight**:
   - If the bug reveals a subtle architectural invariant or edge-case behavior, record it in `insight/<repo>/architecture/gotchas.md` or `insight/<repo>/decisions/`.
8. **Report**: Summarize root cause, fix applied, and tests verified.

## Constraints

- Never apply shotgun fixes or suppress errors with empty catches / `any` casts.
- Always verify with an automated test before closing the issue.
