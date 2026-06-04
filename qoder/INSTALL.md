# Qoder Installation

## Per-project setup

Copy `AGENTS.md` into your project root. Qoder CLI reads it at startup:

```bash
cp qoder/AGENTS.md /path/to/project/AGENTS.md
```

## Global setup

Apply the guidelines across all repositories by copying into `~/.qoder/AGENTS.md`:

```bash
mkdir -p ~/.qoder
cp qoder/AGENTS.md ~/.qoder/AGENTS.md
```

If `~/.qoder/AGENTS.md` already exists, merge the content rather than overwriting. Qoder loads both the user-level and project-level `AGENTS.md` into context at startup.

Start a new Qoder run after adding or changing `~/.qoder/AGENTS.md`; Qoder rebuilds the instruction chain at the start of each run.

## Install skill

Install the reusable guideline skill for use across repositories:

```bash
mkdir -p ~/.qoder/skills
cp -R qoder/skills/karpathy-guidelines ~/.qoder/skills/
```

Qoder discovers skills placed under `~/.qoder/skills/<name>/SKILL.md` automatically. The skill's frontmatter uses `name` and `description`, which Qoder reads to decide when the skill applies.
