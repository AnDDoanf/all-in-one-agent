# Gemini CLI & Antigravity Integration Guide

This directory defines how Google Gemini CLI and Antigravity connect to the shared skills and insight knowledge store.

## Setup
Run:
```bash
pnpm agent:install gemini
```

## Discovery
1. The installer junctions `Agent/skills/` to `.agents/skills/`.
2. Antigravity discovers `.agents/skills/` automatically at project root.
3. `GEMINI.md` instructs the agent to run `Agent/shared/insight-protocol.md` on every task.
