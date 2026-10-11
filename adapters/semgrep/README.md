# semgrep Adapter

Provides semantic code analysis for security vulnerabilities and architectural pattern enforcement.

## Usage in Skills
Used by:
- `security-audit`: Scans for injection flaws, unescaped queries, OWASP vulnerabilities.
- `code-review`: Verifies compliance with custom safety rules.

Findings are saved directly to `insight/<repo>/architecture/security.md`.
