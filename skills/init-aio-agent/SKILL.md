---
name: init-aio-agent
description: Initialize or register the All-in-One Agent architecture after cloning into a parent folder. Non-destructively merges the 17 skills into the parent folder's skills directories, appends entry points (AGENTS.md, CLAUDE.md, GEMINI.md) without replacing existing instructions, and scaffolds the shared insight/ knowledge store.
---

# Init All-In-One Agent (`/init-aio-agent`)

## Purpose & When to Use

Use this skill when:
- The user clones the `all-in-one-agent` repository into a parent directory alongside project repositories (e.g., `workspace/all-in-one-agent/` alongside `workspace/metronome/`, `workspace/anhoc/`, etc.).
- The user invokes `/init-aio-agent` to add this skill library to an existing workspace without losing any existing custom skills, instructions, or rules.

This skill **adds** capabilities to the parent workspace: it merges skills alongside any existing ones and appends agent configuration non-destructively.

---

## Workflow

### Step 1: Detect Parent Workspace & Siblings
1. Identify the parent directory (`../` relative to `all-in-one-agent`).
2. Discover all sibling directories in `../`:
   - Exclude `all-in-one-agent`, hidden directories (`.*`), build/dependency directories (`node_modules`, `dist`, `build`, `target`, `vendor`).
   - Identify candidate source repositories (e.g., `metronome`, `anhoc`, `anchi`).
3. For each detected project, inspect package manifests (`package.json`, `Cargo.toml`, `pyproject.toml`, `go.mod`, etc.) to detect language and framework stack.

### Step 2: Add Skills to Parent Skills Directories (Additive Merging)
The parent workspace may already have custom skills configured for one or more agents. **Never replace or delete existing parent skills.**

1. **Target Agent Skill Locations in Parent**:
   - Gemini CLI / Antigravity: `../.agents/skills/`
   - Claude Code: `../.claude/skills/`
   - OpenAI Codex: `../.codex/skills/`
   - Generic Workspace Skills: `../skills/`

2. **For each skill in `all-in-one-agent/skills/*`**:
   - Check if a skill with that name already exists in the target parent skills directory.
   - **If the skill already exists**: **PRESERVE IT**. Do not overwrite the user's custom skill. Log that the existing skill was preserved.
   - **If the skill does NOT exist**: Link (symlink/junction) or copy the skill directory into the parent skills location.

### Step 3: Non-Destructive Update of Parent Entry Points
If `AGENTS.md`, `CLAUDE.md`, `GEMINI.md`, or `README.md` already exist in the parent directory, **do NOT replace them**. Append or update only within marked All-In-One Agent sections:

```markdown
<!-- ALL_IN_ONE_AGENT_START -->
## All-In-One Agent Skills & Insight Integration
This workspace is equipped with the portable All-In-One Agent skill library and shared knowledge base:
- **Shared Skills**: [all-in-one-agent/skills/](./all-in-one-agent/skills/)
- **Insight Protocol**: [all-in-one-agent/shared/insight-protocol.md](./all-in-one-agent/shared/insight-protocol.md)
- **Knowledge Store**: [insight/](./insight/)

All agents must follow the [Insight Protocol](./all-in-one-agent/shared/insight-protocol.md) before inspecting source code or making modifications.
<!-- ALL_IN_ONE_AGENT_END -->
```

- If the file exists and contains `<!-- ALL_IN_ONE_AGENT_START -->`, update only the content between the start and end markers.
- If the file exists without the marker, append the block to the end of the file.
- If the file does not exist, create it with standard introductory headers plus the block.

### Step 4: Additive Update of Parent `insight/` Knowledge Store
1. Check `../insight/registry.json`:
   - If it already exists: parse existing repositories and append newly discovered sibling projects without removing any existing registered entries.
   - If it does not exist: create `../insight/registry.json` containing all discovered sibling repositories.
2. Ensure `../insight/INDEX.md` exists.
3. For each registered repository, if `../insight/<repo>/` does not exist:
   - Create `../insight/<repo>/INDEX.md`, `manifest.json`, `SPEC.md`.
   - Scaffold subdirectories: `architecture/`, `modules/`, `coding-style/`, `api/`, `database/`, `flows/`, `decisions/`.
   - If `../insight/<repo>/` already exists, **preserve all existing documentation and user edits**.

### Step 5: Verification & Report
1. Verify:
   - All 17 skills from `all-in-one-agent` are available alongside existing parent skills.
   - Pre-existing skills and rules in the parent workspace remain untouched.
   - Entry points cleanly reference both existing rules and the shared skills library.
   - `insight/registry.json` lists all active project repositories.
2. Output a summary:
   - Skills added vs skills preserved.
   - Files appended / updated.
   - Repositories registered in `insight/`.

---

## Constraints

- **Additive Only**: Never delete or overwrite pre-existing skills, rules, or documentation in the parent workspace.
- **Marker-Based Injections**: Always use `<!-- ALL_IN_ONE_AGENT_START -->` / `<!-- ALL_IN_ONE_AGENT_END -->` comments when modifying existing markdown entry points.
- **Portability**: All operations use model tools (`view_file`, `write_to_file`, `replace_file_content`) and standard shell commands without third-party runtime dependencies.
