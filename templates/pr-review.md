# ChatGPT PR Review Checklist

## Context

- Repository / PR:
- Linked Issue and acceptance criteria:
- Repository AGENTS.md and relevant docs:

## Findings (ordered by severity)

For each finding, include the file/path, affected behavior, why it matters and a minimal recommended correction.

## Acceptance criteria

- [ ] Requested behavior is implemented.
- [ ] Constraints and non-goals are respected.
- [ ] Data grain, joins, duplicates, NULLs, UTC boundaries and numerical precision are correct where relevant.
- [ ] Production and credential boundaries remain intact.
- [ ] Diff avoids unrelated scope changes.
- [ ] Tests and CI evidence are sufficient for the risk.

## Validation evidence

List actual tests run and outcomes. Distinguish unrun and blocked checks; do not infer passing tests from code inspection.

## Decision

- Request changes / approve with caveats / ready for user review.
- Residual risks and actions required before merge or deployment.

The final merge and deployment decision belongs to the user.
