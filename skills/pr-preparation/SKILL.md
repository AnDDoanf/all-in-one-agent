---
name: pr-preparation
description: Prepare concise, high-quality pull request summaries, changelog entries, impact assessments, and verification instructions.
---

# PR Preparation

## Required First Step

Read `../shared/insight-protocol.md` and follow it throughout this task.

## Purpose & When to Use

Use this skill when preparing to open a pull request or finalize a branch for team review.

## Workflow

1. **Resolve Repository**: Check target repository in `insight/registry.json`.
2. **Review Git Diff**:
   - Inspect all staged and committed changes on the active branch against base (`main`/`master`).
3. **Cross-Reference Insight**:
   - Read `insight/<repo>/INDEX.md` and `SPEC.md` to articulate the architectural impact.
4. **Compile PR Description**:
   - **Summary**: Concise bullet points explaining *what* changed and *why*.
   - **Architectural Impact**: Note any modified module boundaries, DB migrations, or new API contracts.
   - **Testing & Verification**: Exact commands executed and tests passed.
   - **Breaking Changes**: Explicit warning if existing clients or models are affected.
5. **Synchronize Insight**:
   - If the PR completes a major milestone or ADR, update `insight/<repo>/decisions/` and `INDEX.md`.
6. **Report**: Output the ready-to-paste PR markdown text.

## Constraints

- Do not include raw commit hashes as descriptions; provide meaningful engineering context.
- Keep the summary scannable for human reviewers.
