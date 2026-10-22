# GitHub Issue → Codex → PR Workflow

This workflow defines the handoff between ChatGPT and Codex. GitHub is the persistent **source of task specifications, implementation evidence, and review feedback**.

## 1. Intake and design (ChatGPT)

- Read the **target application's** repository `AGENTS.md`, README, relevant code and authoritative domain documentation.
- Clarify material unknowns, identify the smallest viable change, and define objective acceptance criteria.
- For small, contained tasks, ChatGPT may edit on a branch and create a PR directly; an Issue is optional.

## 2. Issue handoff (ChatGPT → GitHub)

For substantial tasks, create an Issue **in the target application repository**, following [development-issue.md](development-issue.md).

Include objective, technical design, files to inspect, required changes, non-goals, acceptance criteria, verification steps, and expected deliverables. The Issue is the implementation contract for Codex—not a replacement for durable repository instructions.

## 3. Implementation (GitHub → Codex)

The user starts Codex with the target repository and Issue reference. Codex must read:

- The target Issue and its linked specifications.
- Its local global `AGENTS.md` and the **target repository's** `AGENTS.md`.
- Relevant project code and tests.

Codex implements within the agreed scope, runs relevant checks, and opens a PR linked to the Issue. If the plan conflicts with actual code or safety constraints, record the blocker and seek a revised decision rather than silently redesigning the task.

Example kickoff:

```text
Implement issue #42 in owner/repo.
Read the Issue and repository AGENTS.md.
Stay within scope, run relevant tests, and open a PR linked to the Issue.
```

## 4. Review (PR → ChatGPT)

ChatGPT reviews the actual diff, Issue acceptance criteria, and test/CI evidence using [pr-review.md](pr-review.md). Post actionable feedback through the PR. Update the Issue for material requirement or scope changes. Codex addresses review feedback and updates the same PR.

## 5. Approval (User)

The user decides whether to merge or deploy. No Issue, PR approval, or passing CI run automatically grants permission for production database writes, migrations, or deployments.

## Operational notes

- This is a **documented operating procedure**, not automated agent-to-agent messaging.
- ChatGPT needs GitHub access to create Issues and review PRs; Codex needs authorized GitHub access and an explicit instruction to read the Issue.
- Keep actual business definitions and target repository policies with their application code.
- Use bounded tasks and observable acceptance criteria to reduce repeated Codex exploration without skipping verification.
