---
name: frontend-development
description: Build, maintain, and enhance client-side UI components, state stores, and styles following established frontend design systems.
---

# Frontend Development

## Required First Step

Read `../shared/insight-protocol.md` and follow it throughout this task.

## Purpose & When to Use

Use this skill when developing user interfaces, React/Vue/Svelte/Web components, design tokens, hooks, or client state management.

## Workflow

1. **Resolve Repository**: Look up target repository in `insight/registry.json`.
2. **Read Frontend Insight**:
   - Check `insight/<repo>/architecture/frontend.md` for UI framework, CSS strategy, and state management pattern.
   - Check `insight/<repo>/coding-style/conventions.md` for component naming and prop structures.
3. **Inspect Design System**:
   - Check existing component library (e.g. Radix, Tailwind, Vanilla CSS, Styled Components).
   - Use established design tokens (colors, typography, spacing).
4. **Implement UI**:
   - Create or update components with strict semantic markup and accessibility (a11y).
   - Implement responsive layouts and states (loading, error, empty, active).
5. **Verify Locally**:
   - Check component rendering, storybook/tests, and lint rules.
6. **Synchronize Insight**:
   - If new reusable components or design tokens are introduced, document them in `insight/<repo>/architecture/frontend.md`.
7. **Report**: Summarize components built or modified.

## Constraints

- Never introduce a new styling library or state manager if one is already established.
- Avoid inline styles unless dynamic positioning demands it.
