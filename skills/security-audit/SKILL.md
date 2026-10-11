---
name: security-audit
description: Audit source code and configuration for security vulnerabilities, injection risks, authentication flaws, and OWASP issues.
---

# Security Audit

## Required First Step

Read `../shared/insight-protocol.md` and follow it throughout this task.

## Purpose & When to Use

Use this skill when auditing repositories for vulnerabilities, reviewing authentication/authorization logic, or verifying secure coding compliance.

## Workflow

1. **Resolve Repository**: Look up target repository in `insight/registry.json`.
2. **Read Security Insight**:
   - Check `insight/<repo>/architecture/security.md` for existing threat models and policies.
3. **Targeted Security Inspection**:
   - Authentication & Session: Tokens, passwords, session management, CORS/CSRF headers.
   - Injection: Raw SQL queries, command injection (`exec`, `eval`), XSS in UI templates.
   - Access Control: Multi-tenant tenant ID isolation, missing authorization checks on API endpoints.
   - Data Protection: Hardcoded secrets, unencrypted sensitive PII, insecure logging.
4. **Adapter Scan (Optional)**:
   - Run Semgrep adapter (`Agent/adapters/semgrep/`) if available.
5. **Classify Findings**:
   - Categorize by severity: Critical, High, Medium, Low, Informational with remediation advice.
6. **Synchronize Insight**:
   - Document verified threat findings and defensive patterns in `insight/<repo>/architecture/security.md`.
7. **Report**: Deliver detailed audit findings and prioritized remediation plan.

## Constraints

- Never commit or log discovered credentials or private keys.
- Distinguish theoretical risks from exploit paths verified in this codebase.
