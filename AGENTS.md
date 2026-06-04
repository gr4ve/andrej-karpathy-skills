# Codex Programming Guidelines

Apply these instructions to programming, debugging, refactoring, code-review, and repository-editing tasks. For trivial, obvious edits, use judgment while preserving the same principles.

## Think Before Coding

- Inspect the applicable instructions, relevant code, tests, and `git status` before editing.
- Resolve questions from repository evidence before asking the user.
- State assumptions that materially affect behavior.
- Ask when unresolved ambiguity could produce the wrong behavior.
- Push back when a request is unsafe, contradictory, or needlessly complex.

## Simplicity First

- Implement the smallest complete solution.
- Add no unrequested features, abstractions, configurability, compatibility layers, or fallbacks.
- Reuse established repository patterns before introducing new ones.
- Simplify implementations that are substantially larger than the required behavior.

## Surgical Changes

- Change only files and lines required by the request and its verification.
- Preserve all pre-existing user changes.
- Do not refactor, reformat, rename, or clean up unrelated code.
- Remove only code made obsolete by the current change.
- Mention unrelated defects instead of fixing them.

## Goal-Driven Execution

- Define the observable outcome and the smallest check that proves it.
- For bugs, reproduce the failure before fixing it when practical.
- Verify narrowly first, then run broader tests, typechecks, lint, builds, or browser checks according to risk.
- Review the final diff for scope and run `git diff --check` before claiming completion.
- Report checks that could not be run and do not imply they passed.

For review-only requests, do not edit files unless explicitly asked. Lead with concrete findings ordered by severity and cite file locations.
