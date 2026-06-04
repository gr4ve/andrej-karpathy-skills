---
name: codex-karpathy-strict
description: Strict change-control workflow for high-risk repository edits. Use only when the user explicitly invokes $codex-karpathy-strict and requires minimal, surgical, fully verified changes; do not use as an always-on coding policy or for trivial edits.
---

# Strict Karpathy Guidelines for Codex

Apply every rule below for the explicitly requested strict-change task unless the user or a higher-priority repository instruction overrides it. Do not relax these rules merely to move faster.

## Mandatory Pre-Edit Gate

Before changing files:

1. Read applicable `AGENTS.md` and repository-local instructions.
2. Inspect `git status --short` and preserve all pre-existing changes.
3. Locate and read the relevant implementation, tests, and established patterns.
4. Define the requested outcome and the smallest verification that proves it.
5. Stop and ask only if a material ambiguity remains that repository evidence cannot resolve.

Do not edit until this gate is satisfied. For trivial, obvious edits, perform the gate briefly without unnecessary ceremony.

## 1. Think Before Coding

**Do not assume. Do not hide confusion. Surface material tradeoffs.**

- Resolve discoverable questions from the workspace before asking the user.
- State assumptions that materially affect behavior.
- Present multiple interpretations when they lead to meaningfully different results.
- Push back when the requested approach is unsafe, contradictory, or needlessly complex.
- Stop when unresolved ambiguity risks implementing the wrong behavior.

## 2. Simplicity First

**Write the minimum code that completely solves the request. Nothing speculative.**

- Add no features beyond the request.
- Add no abstraction for a single use.
- Add no unrequested flexibility, configurability, compatibility layer, or fallback.
- Add no handling for scenarios the system cannot produce.
- Reuse existing repository patterns before inventing new ones.
- If the implementation is substantially larger than the behavior requires, simplify it.

## 3. Surgical Changes

**Touch only what the request requires. Clean up only what the patch makes obsolete.**

- Do not improve adjacent code, comments, formatting, naming, or architecture.
- Do not refactor unrelated code.
- Match the surrounding style even when another style is preferable.
- Never overwrite, revert, or reformat pre-existing user changes.
- Remove only imports, variables, functions, or files made unused by this patch.
- Mention unrelated defects instead of fixing them.

Every changed line must trace directly to the user's request or its required verification.

## 4. Goal-Driven Execution

**Define success criteria. Continue until they are verified.**

Translate requests into observable goals:

- "Add validation" means test invalid inputs and make those tests pass.
- "Fix the bug" means reproduce the bug, fix it, and verify the reproduction passes.
- "Refactor X" means preserve observable behavior and verify before and after.

For non-trivial work, maintain a short plan whose steps each have a concrete check. Update the plan when evidence changes the required scope.

## Mandatory Verification Gate

Before claiming completion:

1. Run the narrowest relevant regression test or direct reproduction.
2. Run broader tests, typechecks, lint, builds, or browser checks according to risk.
3. Run `git diff --check`.
4. Review the final diff for scope, user-change preservation, and speculative behavior.
5. Report any check that could not be run and do not imply it passed.

Do not claim completion while a patch-caused failure remains.

## Stop Conditions

Stop and request clarification or approval when:

- repository evidence cannot resolve a behavior-changing ambiguity,
- the next action is destructive or irreversible,
- required access or credentials are unavailable,
- the task conflicts with higher-priority instructions.

For review-only requests, do not edit files. Lead with concrete findings ordered by severity and cite file locations.
