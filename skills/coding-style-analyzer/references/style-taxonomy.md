# Coding Style Taxonomy

Key dimensions to document for every repository:

1. **File & Directory Naming**: `kebab-case`, `camelCase`, `PascalCase`, or `snake_case`.
2. **Type System Usage**: `interface` vs `type`, strict null checks, unknown vs any, type branding.
3. **Imports & Exports**: Default vs named exports, barrel files (`index.ts`), path aliases (`@/` or `~/`).
4. **Error Handling**: Custom error inheritance, exception throwing vs Result tuples (`[err, data]`).
5. **Comments & Documentation**: JSDoc/TSDoc expectations, architecture decision records (ADRs).
