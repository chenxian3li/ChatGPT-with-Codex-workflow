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

## Verification and delivery

- Run focused tests, escalating only when needed.
- Never claim a test passed unless it was executed.
- Summarize changed files, validation results, blockers and residual risks.
- Do not merge PRs or deploy without explicit approval.

Project-specific `AGENTS.md` supplies the actual domain rules, paths and test commands. This template is intended for `~/.codex/AGENTS.md` after review.
