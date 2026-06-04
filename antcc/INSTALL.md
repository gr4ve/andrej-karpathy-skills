# AntCC (CodeFuse CLI) Installation

AntCC is a customized Claude Code engine. It reads the same `CLAUDE.md` file but uses different configuration paths (`~/.codefuse/engine/cc/` instead of `~/.claude/`).

## Option A: Plugin

From within AntCC, add the marketplace and install the plugin:

```bash
/plugin marketplace add forrestchang/andrej-karpathy-skills
/plugin install andrej-karpathy-skills@karpathy-skills
```

Plugins are stored under `~/.codefuse/engine/cc/plugins/`.

## Option B: Per-project CLAUDE.md

New project:

```bash
curl -o CLAUDE.md https://raw.githubusercontent.com/forrestchang/andrej-karpathy-skills/main/antcc/CLAUDE.md
```

Existing project (append):

```bash
echo "" >> CLAUDE.md
curl https://raw.githubusercontent.com/forrestchang/andrej-karpathy-skills/main/antcc/CLAUDE.md >> CLAUDE.md
```

## Option C: User-level CLAUDE.md

Apply the guidelines globally. AntCC reads user instructions from `~/.codefuse/engine/cc/CLAUDE.md`:

```bash
mkdir -p ~/.codefuse/engine/cc
curl -o ~/.codefuse/engine/cc/CLAUDE.md https://raw.githubusercontent.com/forrestchang/andrej-karpathy-skills/main/antcc/CLAUDE.md
```

If the file already exists, merge the content rather than overwriting.

## Path-scoped rules

Copy the rules into your project's `.claude/rules/` for path-specific guidance:

```bash
mkdir -p .claude/rules
cp antcc/rules/*.md .claude/rules/
```

AntCC uses the same `.claude/rules/` convention as Claude Code. Rules only load when working with matching files.

## AntCC vs Claude Code path reference

| Item | AntCC | Claude Code |
|------|-------|-------------|
| Settings | `~/.codefuse/engine/cc/settings.json` | `~/.claude/settings.json` |
| Skills | `~/.codefuse/engine/cc/skills/` | `~/.claude/skills/` |
| Plugins | `~/.codefuse/engine/cc/plugins/` | `~/.claude/plugins/` |
| MCP | `~/.codefuse/engine/cc/.claude.json` | `~/.claude.json` |
| Projects | `~/.codefuse/engine/cc/projects/` | `~/.claude/projects/` |
