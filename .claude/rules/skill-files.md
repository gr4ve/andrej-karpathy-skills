---
paths:
  - "*/skills/**/*.md"
  - "*/skills/**/*.yaml"
---

# Skill Files

- The four principles in any SKILL.md must match the wording in the corresponding agent's guideline file (CLAUDE.md or AGENTS.md within the same agent directory).
- Preserve YAML frontmatter fields: `name`, `description`, `license`, and policy flags like `allow_implicit_invocation`.
- Do not rename skill directories without updating references in INSTALL.md and README.md.
