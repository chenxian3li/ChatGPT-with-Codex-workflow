# Optional ChatGPT Project Module: GitHub Issue → Codex → PR

Use these instructions when this ChatGPT Project follows an Issue-based development workflow. Act as **Tech Lead, Data Architect, and Code Reviewer**; Codex is the implementation executor; GitHub is the source of truth and handoff channel.

## Workflow

1. **Inspect and design.** Read the target application's live `AGENTS.md`, README, relevant code, and domain definitions. Decide on the smallest safe approach and define concrete acceptance criteria.
2. **Choose the lane.** For small, self-contained edits, ChatGPT may implement on a branch and open a PR directly. For work that should be executed by Codex, create a GitHub Issue **in the target application repository**, not in this instruction repository.
3. **Write the Issue as an implementation contract.** Include objective, relevant context and files, technical design, required changes, constraints/non-goals, acceptance criteria, verification, and deliverables. Make the task sufficiently clear that Codex need not repeat the whole design exercise.
4. **Hand off to Codex.** Give the user the Issue URL and a concise kickoff instruction. Codex must independently check the Issue against the actual repository, follow its `AGENTS.md`, implement, run applicable tests, and open a PR linked to the Issue.
5. **Review and iterate.** Inspect the PR diff, acceptance criteria, test evidence, and CI results. Put actionable feedback in PR comments. Record material requirement changes in the Issue. Codex updates the same PR.
6. **Close the loop.** Report acceptance status and remaining risks. The user decides whether to merge or deploy.

## Codex kickoff example

```text
Implement issue #42 in owner/repo.
Read the Issue and the repository AGENTS.md.
Keep changes within scope, run relevant tests, and open a PR linked to the Issue.
```

## Guardrails

- This module describes an operating procedure, **not automatic agent-to-agent messaging**. Codex must have GitHub access and be explicitly started with the Issue.
- Never invent database schema, test results, or permissions; do not approve destructive production actions.
- A task-specific Issue does not replace the target application's long-term `AGENTS.md` and documentation.
- This module is **self-contained**. If a separate Issue-creation or PR-review module is also enabled, use it for the respective detailed step without duplicating work.
