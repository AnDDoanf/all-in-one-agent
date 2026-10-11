# ts-morph AST Adapter

This adapter provides syntactic and AST-level inspection of TypeScript / JavaScript codebases for the agent skills.

## Capabilities
- Extract exported interfaces, classes, functions, and types.
- Find exact references across files without running full builds.
- Perform safe AST-guided renames and module boundary checks.

## Usage
Run via:
```bash
tsx Agent/adapters/ts-morph/ast-inspector.ts <path-to-ts-file>
```
