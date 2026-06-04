---
name: codex-karpathy-workflow
description: Evidence-driven repository change workflow for Codex. Use for non-trivial code implementation, bug fixes, refactoring, or reviews that need targeted exploration, minimal patches, user-change preservation, and layered verification; do not use for simple questions or non-code tasks.
---

# Codex Karpathy Workflow

Turn the Karpathy guidelines into an evidence-driven Codex execution loop. Treat the repository, its instructions, and its tests as the source of truth.

## Core Rules

- Discover before asking. Resolve uncertainty by reading repository instructions, code, tests, configuration, and history first.
- Ask only when an unresolved choice materially changes behavior, requires unavailable user intent, or risks destructive or irreversible action.
- Prefer the smallest complete change. Do not add speculative features, abstractions, compatibility layers, or unrelated cleanup.
- Preserve user work. Treat pre-existing dirty files and unfamiliar changes as intentional unless the user says otherwise.
- Match the repository's established patterns before introducing a new one.
- Claim only what verification evidence supports.

## Execute the Workflow

### 1. Define the Outcome

Translate the request into:

- the observable behavior that must change,
- constraints and explicit non-goals,
- the smallest useful verification that proves completion.

For a multi-step task, maintain a short plan with verifiable steps. For a trivial, obvious edit, skip planning ceremony and proceed directly.

### 2. Gather Targeted Evidence

Before editing:

1. Read applicable `AGENTS.md` and repository-local instructions.
2. Inspect `git status --short` to identify user changes that must be preserved.
3. Use `rg` or `rg --files` to locate the implementation, related tests, and established patterns.
4. Read only the files needed to understand the behavior and likely blast radius.

Use parallel read-only tool calls when the investigations are independent. Do not bulk-read the repository or ask the user for facts that the workspace can answer.

### 3. Choose the Smallest Complete Patch

Select an approach that:

- changes only files directly required by the request,
- reuses existing helpers and conventions,
- avoids a new abstraction for a single use,
- includes tests when behavior changes or regression risk warrants them.

Surface assumptions only when they affect the result. If two viable approaches remain, choose the simpler reversible one unless the choice has meaningful product or compatibility consequences.

### 4. Implement Surgically

Before editing, briefly state what will change. Then:

- use `apply_patch` for manual edits,
- keep formatting and naming consistent with surrounding code,
- remove only imports, variables, or code made obsolete by the patch,
- leave unrelated defects or dead code untouched,
- never overwrite, revert, or reformat pre-existing user changes.

If implementation reveals that the planned scope is wrong, pause and update the plan before expanding it.

### 5. Verify in Layers

Run the cheapest relevant checks first, then broaden according to risk:

1. focused regression test or direct reproduction,
2. nearby test suite, typecheck, lint, or build,
3. browser verification for significant frontend behavior when a local target is available,
4. `git diff --check` and a final diff review.

During the final diff review, confirm:

- every changed line traces to the request,
- no user changes were lost,
- no speculative behavior was added,
- tests exercise the changed behavior,
- comments and docs remain accurate.

Fix failures caused by the patch and rerun the relevant checks. Clearly report checks that could not be run.

### 6. Report Evidence

Finish with a concise account of:

- what behavior changed,
- what verification passed,
- any unresolved risk or unverified condition.

Do not report planned work as completed or imply broader coverage than the checks provide.

## Review-Only Tasks

When the user asks for a review, do not edit unless explicitly asked. Lead with concrete findings ordered by severity, cite file locations, and distinguish confirmed bugs from residual risks or missing tests.
