# Codex Integration Guide

This directory defines how OpenAI Codex connects to the shared skills and insight knowledge store.

## Setup
Run:
```bash
pnpm agent:install codex
```

## How Codex Discovers Skills
1. The installer creates a junction from `Agent/skills/` to `.codex/skills/`.
2. Instructions in `AGENTS.md` and `.codex/instructions.md` direct Codex to follow `Agent/shared/insight-protocol.md`.
3. Codex reads `insight/<repo>/INDEX.md` prior to code modifications.
