---
name: code-review
description: Review pull requests, diffs, or code changes against repository architectural rules, coding standards, and security requirements.
---

# Code Review

## Required First Step

Read `../shared/insight-protocol.md` and follow it throughout this task.

## Purpose & When to Use

Use this skill when:
- Reviewing a branch diff or pull request.
- Auditing newly implemented features for compliance before merging.
- Ensuring code follows repository-specific architectural boundaries and style conventions.

## Workflow

1. **Resolve Target Repository**: Locate entry in `insight/registry.json`.
2. **Read Insight**:
   - Check `insight/<repo>/coding-style/conventions.md`.
   - Check `insight/<repo>/architecture/system-overview.md`.
   - Check `insight/<repo>/architecture/security.md` (if security-relevant).
3. **Inspect Diff**:
   - Check modified files and identify touched modules.
   - Cross-reference with module boundaries documented in `insight/<repo>/modules/`.
4. **Evaluate Compliance**:
   - Architecture: Does the change violate module boundaries or create illegal circular dependencies?
   - Style: Does it match the documented conventions?
   - Correctness & Tests: Are new edge cases covered by automated tests?
   - Security: Are inputs sanitized? Any OWASP top 10 violations?
5. **Generate Constructive Review**:
   - Categorize comments into: `[Blocking]`, `[Warning]`, `[Suggestion]`, `[Praise]`.
   - Cite exact file lines and documented insight rules.
6. **Synchronize Insight (If Applicable)**:
   - If a new architectural pattern or rule was established and verified during review, document it in `insight/<repo>/decisions/`.
7. **Report**: Deliver review findings clearly.

## Constraints

- Do not nitpick stylistic preferences that contradict `insight/<repo>/coding-style/`.
- Do not make assumptions without referencing source lines.
