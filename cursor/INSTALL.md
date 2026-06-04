# Cursor Installation

## In this repository

1. Open the folder in Cursor.
2. Copy `karpathy-guidelines.mdc` into `.cursor/rules/`:

```bash
mkdir -p .cursor/rules
cp cursor/karpathy-guidelines.mdc .cursor/rules/
```

3. Confirm it under **Settings → Rules**, where `karpathy-guidelines` should appear with `alwaysApply: true`.

## Use in another project

Copy `karpathy-guidelines.mdc` into the target project's `.cursor/rules/` directory:

```bash
mkdir -p /path/to/project/.cursor/rules
cp cursor/karpathy-guidelines.mdc /path/to/project/.cursor/rules/
```

Adjust or merge with existing rules as needed.

## Personal Agent Skills

To make the guidelines available as a reusable skill under `~/.cursor/skills`, copy the file:

```bash
mkdir -p ~/.cursor/skills/karpathy-guidelines
cp cursor/karpathy-guidelines.mdc ~/.cursor/skills/karpathy-guidelines/
```
