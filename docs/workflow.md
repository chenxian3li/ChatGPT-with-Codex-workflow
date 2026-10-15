# Development workflow

## 1. Intake and discovery

The user states the desired outcome. ChatGPT reads the repository's README, AGENTS.md, relevant code and domain references. Surface material unknowns and avoid inventing database schema or metric definitions.

## 2. Choose an implementation lane

- **Direct ChatGPT + GitHub:** small, contained, reviewable tasks; make changes in a branch and create a PR.
- **Codex handoff:** multi-file, complex or environment-dependent tasks; ChatGPT first produces a scoped design and a GitHub Issue based on the [development issue template](../templates/development-issue.md).

## 3. Execution

Codex reads the Issue, repository AGENTS.md, relevant documentation and local global instructions. It implements narrowly, verifies against acceptance criteria, runs focused tests, and opens a PR referencing the Issue. Unknowns affecting correctness are raised explicitly.

## 4. Review loop

ChatGPT inspects the actual PR diff, linked Issue, CI results and test evidence with the [review template](../templates/pr-review.md). Report actionable findings and return them to Codex through PR comments. Repeat until acceptable.

## 5. Completion

The user makes the final merge/deploy decision. Do not assume PR approval authorizes database writes, migrations, production deployment or release.

## Handoff contract

Each substantial Issue should include: objective, context, technical design, required changes, constraints/non-goals, acceptance criteria, verification and deliverables.

## Cost control

Prioritize bounded tasks, known file pointers and deterministic acceptance criteria. Avoid speculative refactors or repeated planning in Codex. Do not skip necessary safety checks or validation to minimize cost.
