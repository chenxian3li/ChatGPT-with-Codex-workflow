# Architecture and ownership

## Objective

Move expensive exploratory reasoning, design and review to ChatGPT. Give Codex a scoped implementation contract so that simpler execution models can make effective progress without repeatedly rediscovering requirements.

## Actors

- **User:** states business goals and approves merge/deploy actions.
- **ChatGPT:** Tech Lead, Data Architect, Reviewer. Consults repository rules and current code; defines scope, plan, acceptance criteria and review feedback.
- **Codex:** Executor. Implements the planned change, validates assumptions against source, runs tests, reports blockers and opens PRs.
- **GitHub:** canonical storage and collaboration substrate, including instructions, Issues, PRs, code and CI results.

## Instruction layers

- ChatGPT Custom Instructions: durable personal preferences.
- ChatGPT Project Instructions: specific planning and reviewing behavior.
- Codex global AGENTS.md: common implementation principles.
- Application repository AGENTS.md: authoritative project constraints and pointers to definitions and verification.
- Issue and PR: task-specific handoff and result/evidence, **not** enduring policy.

This configuration repository is the **source of truth for shared configuration templates**. Each application's own repository remains the **source of truth for its AGENTS.md and domain contracts**.

## Ownership boundaries

- ChatGPT may make contained changes itself and open a PR.
- Codex may challenge inconsistent or unsafe specifications, but should record blockers instead of silently redesigning scope.
- Review feedback goes into PR conversations; requirement changes must be reflected in the Issue or other canonical specification.
- Changes must never bypass permission, data safety or deployment controls.

## Synchronization

The files under `chatgpt/` do not automatically update the ChatGPT UI. The file under `codex/` does not automatically update a Mac's `~/.codex/AGENTS.md`. Explicit installation/synchronization is required.
