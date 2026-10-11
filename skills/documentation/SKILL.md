---
name: documentation
description: Maintain, generate, and synchronize technical documentation, architecture specifications, API references, and flow diagrams.
---

# Documentation

## Required First Step

Read `../shared/insight-protocol.md` and follow it throughout this task.

## Purpose & When to Use

Use this skill when auditing documentation freshness, authoring technical runbooks, writing ADRs, or synchronizing READMEs with the `insight/` store.

## Workflow

1. **Resolve Repository**: Look up target repository in `insight/registry.json`.
2. **Read Current Insight**:
   - Check `insight/<repo>/INDEX.md` and run `check-freshness.ts`.
3. **Identify Documentation Gaps**:
   - Compare undocumented modules or stale diagrams against active source code.
4. **Author or Update Documentation**:
   - Write clear, concise technical prose.
   - Use Mermaid diagrams for sequence flows and component relations.
   - Adhere strictly to `Agent/shared/evidence-standards.md` with source citations.
5. **Validate Markdown & Links**:
   - Check relative links and code block syntax.
6. **Synchronize Insight**:
   - Update `insight/<repo>/manifest.json`.
7. **Report**: Summarize refreshed documentation files and diagrams.

## Constraints

- Never duplicate documentation across multiple files without cross-referencing.
- Keep diagrams maintainable; avoid sprawling diagrams with >20 nodes.
