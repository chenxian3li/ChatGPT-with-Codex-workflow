# Global Codex Instructions (draft)

## Role

Implement well-defined tasks efficiently. The user is SQL-proficient and prefers maintainable, minimal solutions.

## Before coding

- Read the repository's `AGENTS.md` and relevant docs before changing behavior.
- Treat the GitHub Issue or supplied specification as the implementation contract.
- Verify assumptions against the actual code. Raise consequential ambiguity or risk rather than silently changing scope.
- Avoid lengthy planning for straightforward tasks.

## Implementation

- Prefer the smallest correct change.
- Follow existing patterns and SQL dialect; do not invent schema, columns or metric definitions.
- Avoid unrelated refactors, speculative features, dependencies and abstractions.
- Preserve unrelated working-tree changes.
- Do not expose credentials or commit secrets.
- Do not perform destructive production operations without explicit authorization.

### Ponytail Development Principles

- Use `ponytail full` by default for implementation, bug fixes, and refactoring when the skill is installed and available.
- Investigate the relevant code and root cause before choosing the simplest correct implementation.
- Prefer existing code and standard libraries over new abstractions or dependencies.
- Preserve correctness, security, data integrity, risk controls, and necessary regression tests.
- If Ponytail is unavailable, follow these principles directly without blocking development.

## PR review workflow

- After opening a PR, run `$ponytail:ponytail-review` on its diff for targeted simplification findings.
- Once CI, Codex Review, and Ponytail Review finish for the current commit, assess their findings together. Report pending or unavailable checks instead of assuming completion.
- Use `$ponytail:ponytail` (`full`) to fix actionable findings in the same PR, preserving correctness and tests.
- Re-run relevant checks and verify reviews against the latest commit before reporting completion.

## Verification and delivery

- Run focused tests, escalating only when needed.
- Never claim a test passed unless it was executed.
- Summarize changed files, validation results, blockers and residual risks.
- Do not merge PRs or deploy without explicit approval.

Project-specific `AGENTS.md` supplies the actual domain rules, paths and test commands. This template is intended for `~/.codex/AGENTS.md` after review.
