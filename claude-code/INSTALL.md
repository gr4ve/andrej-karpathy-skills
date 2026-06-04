# Claude Code Installation

## Option A: Plugin (recommended)

From within Claude Code, add the marketplace and install the plugin:

```bash
/plugin marketplace add forrestchang/andrej-karpathy-skills
/plugin install andrej-karpathy-skills@karpathy-skills
```

This makes the guidelines available across all your projects as a Claude Code plugin.

## Option B: Per-project CLAUDE.md

New project:

```bash
curl -o CLAUDE.md https://raw.githubusercontent.com/forrestchang/andrej-karpathy-skills/main/claude-code/CLAUDE.md
```

Existing project (append):

```bash
echo "" >> CLAUDE.md
curl https://raw.githubusercontent.com/forrestchang/andrej-karpathy-skills/main/claude-code/CLAUDE.md >> CLAUDE.md
```

## Option C: User-level CLAUDE.md

Apply the guidelines globally by adding to `~/.claude/CLAUDE.md`:

```bash
curl -o ~/.claude/CLAUDE.md https://raw.githubusercontent.com/forrestchang/andrej-karpathy-skills/main/claude-code/CLAUDE.md
```

If `~/.claude/CLAUDE.md` already exists, merge the content rather than overwriting.

## Path-scoped rules

Copy the `rules/` directory into your project's `.claude/rules/` for path-specific guidance:

```bash
mkdir -p .claude/rules
cp claude-code/rules/*.md .claude/rules/
```

These rules only load into context when Claude works with matching files, saving context space.
