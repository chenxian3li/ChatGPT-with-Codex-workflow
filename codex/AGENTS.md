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

## Pull request review and findings resolution

After creating a pull request:

1. **Targeted Ponytail review.** Invoke the installed `$ponytail:ponytail-review` skill on the PR diff against its base branch. Focus on changed code and immediately related paths. Report actionable over-engineering and simplification findings only; this does not replace a correctness or security review. Record findings (or no findings) and the reviewed head commit.
2. **Collect the review gate.** Check all required CI jobs, the GitHub Codex Review, and Ponytail Review for the same PR head commit. Do not start the findings-fix phase until all three have produced final results. A failed CI job is a completed result that needs fixing; a pending or absent review is not. If any check or skill is unavailable, report the blocker and stop rather than claiming it ran or waiting indefinitely.
3. **Triage before fixing.** Consolidate the results. Prioritize correctness, security, data integrity, regression risks, and failed CI. Accept Ponytail simplifications only when they preserve required behavior and appropriate tests. Explain why any finding is deferred, disputed, or not actionable.
4. **Repair with Ponytail.** Invoke the installed `$ponytail:ponytail` skill (full intensity) to address actionable findings with the smallest root-cause changes. If no actionable findings exist, avoid unnecessary edits. Keep fixes within the same PR; do not introduce unrelated refactoring.
5. **Reverify the updated PR.** Run relevant tests and checks, then inspect CI and available reviews for the *latest* head commit. Prior results do not validate a new commit. If new findings or missing checks prevent sign-off, report their status; do not enter an unbounded review-fix loop.

These instructions guide the active Codex session; they do not schedule background work or guarantee that asynchronous GitHub reviews will finish while Codex is running. Do not claim review completion without evidence, and do not merge or deploy without explicit user approval.

## Verification and delivery

- Run focused tests, escalating only when needed.
- Never claim a test passed unless it was executed.
- Summarize changed files, validation results, blockers and residual risks.
- Do not merge PRs or deploy without explicit approval.

Project-specific `AGENTS.md` supplies the actual domain rules, paths and test commands. This template is intended for `~/.codex/AGENTS.md` after review.
