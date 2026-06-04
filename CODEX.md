# Using this repo with Codex

The root [`AGENTS.md`](AGENTS.md) contains persistent Karpathy-inspired programming guidelines. Codex reads it before starting work in this repository, so programming, debugging, refactoring, and code-review tasks follow the principles without relying on skill invocation.

This repository includes two Codex-specific skills:

- [`.agents/skills/codex-karpathy-strict/SKILL.md`](.agents/skills/codex-karpathy-strict/SKILL.md) applies strict change-control gates when explicitly invoked.
- [`.agents/skills/codex-karpathy-workflow/SKILL.md`](.agents/skills/codex-karpathy-workflow/SKILL.md) provides a pragmatic evidence-driven workflow for non-trivial repository changes.

Codex discovers both skills automatically when launched inside this repository because repository skills live under `.agents/skills`.

These locations and metadata follow the official [Codex Agent Skills documentation](https://developers.openai.com/codex/skills).

## Apply the guidelines globally

To use the same programming guidelines across repositories, merge [`AGENTS.md`](AGENTS.md) into `~/.codex/AGENTS.md`. Codex reads the global file first, then layers repository and nested instructions on top.

Do not overwrite an existing global file without merging its instructions. Use `~/.codex/AGENTS.override.md` only for temporary global overrides.

The discovery and precedence behavior follows the official [Codex AGENTS.md documentation](https://developers.openai.com/codex/guides/agents-md).

Start a new Codex run after adding or changing `AGENTS.md`; Codex rebuilds the instruction chain at the start of each run.

## Install as personal skills

Install either skill for use across repositories by copying or symlinking it into `$HOME/.agents/skills`:

```bash
mkdir -p "$HOME/.agents/skills"
ln -s /path/to/andrej-karpathy-skills/.agents/skills/codex-karpathy-strict \
  "$HOME/.agents/skills/codex-karpathy-strict"
```

Invoke it explicitly with `$codex-karpathy-strict`.

The strict skill sets `policy.allow_implicit_invocation: false` because strict behavior should not hijack unrelated tasks. The standard workflow remains eligible for implicit invocation when its focused description matches.

## Enforce the guidelines per project

For persistent project-wide behavior, copy or adapt this repository's root [`AGENTS.md`](AGENTS.md) into the target project's root. Official Codex guidance assigns always-on repository conventions to `AGENTS.md`, while skills package reusable task workflows.

Direct skill folders are appropriate while authoring and iterating locally. Package the skills as a Codex plugin when publishing them as a stable installable bundle.

## Claude Code, Cursor, and Codex

- **Claude Code:** Install the plugin or use [`CLAUDE.md`](CLAUDE.md).
- **Cursor:** Use [`.cursor/rules/karpathy-guidelines.mdc`](.cursor/rules/karpathy-guidelines.mdc), which has `alwaysApply: true`.
- **Codex:** Root `AGENTS.md` supplies persistent programming behavior; `.agents/skills` supplies reusable workflows.
- **Qoder:** User-level `~/.qoder/AGENTS.md` and project-level root `AGENTS.md` supply persistent programming behavior; `~/.qoder/skills` supplies the reusable guideline skill. See [`QODER.md`](QODER.md).

## For contributors

Keep the four core principles aligned across [`CLAUDE.md`](CLAUDE.md), [`.cursor/rules/karpathy-guidelines.mdc`](.cursor/rules/karpathy-guidelines.mdc), [`AGENTS.md`](AGENTS.md), and [`.agents/skills/codex-karpathy-strict/SKILL.md`](.agents/skills/codex-karpathy-strict/SKILL.md). Codex-specific instructions may remain stricter where they express Codex tool and verification behavior.
