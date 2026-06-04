# Using this repo with Qoder

The user-level `~/.qoder/AGENTS.md` file contains persistent Karpathy-inspired programming guidelines. Qoder CLI reads it at startup for every project, so programming, debugging, refactoring, and code-review tasks follow the principles globally without relying on skill invocation.

Qoder also loads a project-level `AGENTS.md` from the repository root. This repository's root [`AGENTS.md`](AGENTS.md) supplies the same principles per project.

## Apply the guidelines globally

To use the same programming guidelines across repositories, copy this repository's root [`AGENTS.md`](AGENTS.md) into `~/.qoder/AGENTS.md`:

```bash
mkdir -p "$HOME/.qoder"
cp AGENTS.md "$HOME/.qoder/AGENTS.md"
```

Do not overwrite an existing global file without merging its instructions. If `~/.qoder/AGENTS.md` already exists, append or merge the four principles rather than replacing the file.

Start a new Qoder run after adding or changing `~/.qoder/AGENTS.md`; Qoder rebuilds the instruction chain at the start of each run.

## Apply the guidelines per project

For persistent project-wide behavior, copy this repository's root [`AGENTS.md`](AGENTS.md) into the target project's root. Qoder loads both the user-level and project-level `AGENTS.md` into context at startup.

## Install as a personal skill

Install the reusable guideline skill for use across repositories by copying it into `~/.qoder/skills`:

```bash
mkdir -p "$HOME/.qoder/skills"
cp -R skills/karpathy-guidelines "$HOME/.qoder/skills/karpathy-guidelines"
```

Qoder discovers skills placed under `~/.qoder/skills/<name>/SKILL.md` automatically. The skill's frontmatter uses `name` and `description`, which Qoder reads to decide when the skill applies.

## Claude Code, Cursor, Codex, and Qoder

- **Claude Code:** Install the plugin or use [`CLAUDE.md`](CLAUDE.md).
- **Cursor:** Use [`.cursor/rules/karpathy-guidelines.mdc`](.cursor/rules/karpathy-guidelines.mdc), which has `alwaysApply: true`.
- **Codex:** Root [`AGENTS.md`](AGENTS.md) supplies persistent programming behavior; `.agents/skills` supplies reusable workflows. See [`CODEX.md`](CODEX.md).
- **Qoder:** User-level `~/.qoder/AGENTS.md` and project-level root `AGENTS.md` supply persistent programming behavior; `~/.qoder/skills` supplies the reusable guideline skill.

## For contributors

Keep the four core principles aligned across [`CLAUDE.md`](CLAUDE.md), [`.cursor/rules/karpathy-guidelines.mdc`](.cursor/rules/karpathy-guidelines.mdc), [`AGENTS.md`](AGENTS.md), [`skills/karpathy-guidelines/SKILL.md`](skills/karpathy-guidelines/SKILL.md), and [`.agents/skills/codex-karpathy-strict/SKILL.md`](.agents/skills/codex-karpathy-strict/SKILL.md). Qoder reuses the root `AGENTS.md` and the shared skill, so no Qoder-specific principle file needs separate maintenance.
