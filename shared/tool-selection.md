# Tool Selection Matrix

Agents have access to various built-in commands and specialized adapters. Use the right tool for the right job to avoid token waste and performance bottlenecks.

---

## 1. Tool Selection Decision Guide

```
Is the task asking for syntactic/type verification?
 ├── YES ──> Use ts-morph AST Adapter (Agent/adapters/ts-morph)
 └── NO  ──> Is the task finding references or text occurrences?
              ├── YES ──> Use Grep / Ripgrep (grep_search)
              └── NO  ──> Is the task mapping module dependencies?
                           ├── YES ──> Use dependency-cruiser Adapter
                           └── NO  ──> Is the task checking security/anti-patterns?
                                        ├── YES ──> Use Semgrep Adapter
                                        └── NO  ──> Is the task visualizing flows?
                                                     └── YES ──> Mermaid Adapter
```

---

## 2. Adapter Catalog

| Adapter | Directory | Best Used For | Fallback if Adapter Not Installed |
|---|---|---|---|
| **ts-morph** | `Agent/adapters/ts-morph/` | Precise TypeScript AST exploration, class hierarchies, interface extraction, and refactor renames. | Regex search + compiler `tsc --noEmit` check. |
| **dependency-cruiser** | `Agent/adapters/dependency-cruiser/` | Circular dependency checks, module boundary validation, architectural layering. | Import grep scanning + manual link review. |
| **semgrep** | `Agent/adapters/semgrep/` | Security flaw scanning (OWASP, SQLi, XSS, insecure deserialization) and custom policy rules. | Manual regex search for sensitive API patterns. |
| **mermaid** | `Agent/adapters/mermaid/` | Architecture charts, sequence diagrams, ERDs, and state machines embedded in insight docs. | Standard ASCII diagrams or Markdown tables. |
| **openapi** | `Agent/adapters/openapi/` | Extracting and validating OpenAPI/Swagger contracts for REST APIs. | Route file manual inspection. |

---

## 3. Best Practices
- **Prefer Cached Insight First**: Never invoke heavy AST or static analysis tools if the target artifact is already documented and verified in `insight/<repo>/`.
- **Targeted Scope**: When running adapters or search tools, scope them to the specific module directory rather than the whole workspace.
