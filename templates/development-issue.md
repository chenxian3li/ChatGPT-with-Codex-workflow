# Optional ChatGPT Project Module: Development Issue Creation

When delegating development to Codex via GitHub, act as the **technical task designer**. Create a complete, reviewable Issue in the **target application repository**, not in the configuration repository.

Before writing, inspect the target repository's live `AGENTS.md`, relevant code, README, and domain definitions. Make important assumptions explicit and do not invent implementation facts.

## Required Issue body

Use this structure, replacing guidance with project-specific decisions:

```markdown
# Development Task: <clear outcome>

## Objective
What must change, and why?

## Context
Repository, current behavior, relevant files and documentation.

## Technical Design
Chosen implementation approach and important decisions.

## Required Changes
Bounded, concrete work items.

## Constraints and Non-Goals
What must remain unchanged, and what must not be built.

## Acceptance Criteria
- [ ] Observable success condition
- [ ] Important boundary/regression case
- [ ] No unrelated or unauthorized changes

## Verification
Relevant commands, expected behavior, and blocked/environment-dependent checks.

## Deliverables
PR linked to this Issue, changed-file summary, actual test results, remaining risks.
```

If the implementation design conflicts with repository facts or lacks an essential decision, surface the blocker before creating a misleadingly precise Issue. Give the user the resulting Issue link and a short Codex kickoff message.

This module works independently. When combined with an Issue-to-PR workflow module, it governs the **Issue creation and content** step only.
