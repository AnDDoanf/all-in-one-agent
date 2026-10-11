# AGENTS.md — Global Multi-Agent Instructions (All-In-One Agent)

This repository is a **portable, standalone collection of agent skills** designed to operate across **Codex**, **Claude Code**, and **Gemini CLI**.

When placed into a parent workspace, all agents share these exact skills and read/write the parent workspace's `../insight/` knowledge base.

---

## 1. The Fundamental Rule

> **Every skill reads the relevant repository insight (`../insight/<repo>/`) before working. It inspects source code only when required, and updates the shared insight when its work changes the documented knowledge.**

---

## 2. Shared Protocol

Every skill adheres strictly to:
- [`shared/insight-protocol.md`](./shared/insight-protocol.md)
- [`shared/evidence-standards.md`](./shared/evidence-standards.md)
- [`shared/update-policy.md`](./shared/update-policy.md)
- [`shared/tool-selection.md`](./shared/tool-selection.md)

---

## 3. Skills Inventory (17 Skills)

Located in [`skills/`](./skills/):
- [`init-aio-agent`](./skills/init-aio-agent/SKILL.md): Initializes parent workspace, auto-detects sibling repos, creates entry points and `insight/`.
- [`codebase-explorer`](./skills/codebase-explorer/SKILL.md): Discovers architecture, modules, boundaries, and dependencies.
- [`coding-style-analyzer`](./skills/coding-style-analyzer/SKILL.md): Analyzes code patterns, idioms, naming, and lint rules.
- [`feature-implementation`](./skills/feature-implementation/SKILL.md): Implements features using documented patterns.
- [`code-review`](./skills/code-review/SKILL.md): Reviews PRs and diffs against architectural rules.
- [`test-generator`](./skills/test-generator/SKILL.md): Creates unit, integration, and contract tests.
- [`debugging`](./skills/debugging/SKILL.md): Investigates root causes using data flows.
- [`frontend-development`](./skills/frontend-development/SKILL.md): Builds UI components and design systems.
- [`api-development`](./skills/api-development/SKILL.md): Develops API routes and request contracts.
- [`database-migration`](./skills/database-migration/SKILL.md): Designs schemas, migrations, and ORM models.
- [`refactoring`](./skills/refactoring/SKILL.md): Restructures code safely without changing external behavior.
- [`security-audit`](./skills/security-audit/SKILL.md): Audits vulnerabilities, injection, and authorization.
- [`performance-optimization`](./skills/performance-optimization/SKILL.md): Analyzes bottlenecks, queries, and caching.
- [`pr-preparation`](./skills/pr-preparation/SKILL.md): Prepares PR summaries and impact assessments.
- [`dependency-management`](./skills/dependency-management/SKILL.md): Audits, updates, and manages dependencies.
- [`documentation`](./skills/documentation/SKILL.md): Synchronizes technical documentation and diagrams.
- [`migration-assistant`](./skills/migration-assistant/SKILL.md): Guides multi-phase version and framework migrations.
