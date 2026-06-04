---
paths:
  - "claude-code/plugin/**"
---

# Plugin Config

- `plugin.json` and `marketplace.json` must stay consistent: name, version, and description should match.
- Do not change `owner`, `id`, or `category` without explicit instruction.
- The `skills` path in `plugin.json` must point to a valid skill directory.
