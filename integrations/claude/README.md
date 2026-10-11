# Claude Code Integration Guide

This directory defines how Anthropic's Claude Code connects to the shared skills and insight knowledge store.

## Setup
Run:
```bash
pnpm agent:install claude
```

## How Claude Code Discovers Skills
1. The installer junctions `Agent/skills/` to `.claude/skills/`.
2. `CLAUDE.md` in the workspace root instructs Claude Code to adopt the shared insight protocol.
3. Persistent discoveries are synchronized directly back to `insight/<repo>/`.
