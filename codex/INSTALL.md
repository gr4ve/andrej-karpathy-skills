# Codex Installation

## Per-project setup

Copy `AGENTS.md` into your project root. Codex reads it before starting work in the repository:

```bash
cp codex/AGENTS.md /path/to/project/AGENTS.md
```

## Global setup

Apply the guidelines across all repositories by merging into `~/.codex/AGENTS.md`:

```bash
mkdir -p ~/.codex
cp codex/AGENTS.md ~/.codex/AGENTS.md
```

If `~/.codex/AGENTS.md` already exists, merge the content rather than overwriting. Codex reads the global file first, then layers repository and nested instructions on top.

Start a new Codex run after adding or changing `AGENTS.md`; Codex rebuilds the instruction chain at the start of each run.

## Install skills

Install either skill for use across repositories by copying into `$HOME/.agents/skills`:

```bash
mkdir -p "$HOME/.agents/skills"
cp -R codex/skills/codex-karpathy-strict "$HOME/.agents/skills/"
cp -R codex/skills/codex-karpathy-workflow "$HOME/.agents/skills/"
```

- **codex-karpathy-strict**: Strict change-control gates. Invoke explicitly with `$codex-karpathy-strict`. Policy `allow_implicit_invocation: false` prevents it from hijacking unrelated tasks.
- **codex-karpathy-workflow**: Pragmatic evidence-driven workflow. Eligible for implicit invocation when its description matches.

The discovery and precedence behavior follows the official [Codex AGENTS.md documentation](https://developers.openai.com/codex/guides/agents-md) and [Codex Agent Skills documentation](https://developers.openai.com/codex/skills).
