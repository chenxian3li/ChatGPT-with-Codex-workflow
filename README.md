# ChatGPT with Codex — Development Collaboration Framework

A **ChatGPT-led development workflow** that separates technical leadership from code execution. GitHub acts as the **source of truth and communication channel**, not as a decision-making agent.

> Status: **Architecture scaffold / draft templates**. Instructions in this repository are starting points; they are **not automatically synchronized** to ChatGPT settings or local Codex configuration.

## 1. Roles and responsibilities

```mermaid
flowchart TB
    U["User<br/>Business goals and approval"]
    G["ChatGPT<br/>Tech Lead · Data Architect · Code Reviewer<br/>Requirements, design, task breakdown, acceptance, review"]
    C["Codex<br/>Software Engineer · Executor<br/>Implementation, tests, fixes, PRs"]
    H[("GitHub<br/>Source of Truth + Communication<br/>Docs · AGENTS.md · Issues · PRs · CI")]
    U -->|"Request / prioritization"| G
    G -->|"Issue: implementation contract"| H
    H -->|"Issue + repository instructions"| C
    C -->|"Commits, PR, test evidence"| H
    H -->|"Diff, review context, CI"| G
    G -->|"Review / feedback"| H
    G -->|"Recommendation"| U
    U -->|"Merge / deployment decision"| H
```

**Decision boundary:** ChatGPT proposes design and reviews delivery; Codex executes within the agreed scope, validates against real code, and flags blockers rather than silently changing architecture. The user controls final merge and deployment.

## 2. Standard development workflow

```mermaid
flowchart TD
    A["User submits a request"] --> B["ChatGPT inspects repository and requirements"]
    B --> D{"Scope and risk?"}
    D -->|"Simple, contained change"| E["ChatGPT + GitHub<br/>Edit on feature branch, create PR"]
    D -->|"Complex or multi-file change"| F["ChatGPT drafts technical design<br/>Acceptance criteria + non-goals"]
    F --> G["GitHub Issue<br/>Persistent handoff contract"]
    G --> H["Codex reads Issue and AGENTS.md<br/>Implements + verifies + creates PR"]
    E --> I["ChatGPT reviews PR<br/>Diff + acceptance criteria + CI"]
    H --> I
    I --> J{"Accepted?"}
    J -->|"Changes needed"| K["Review comments / Issue updates"]
    K --> H
    J -->|"Yes"| L["User approves merge / deployment"]
```

For small requests, a GitHub Issue is optional; a PR still provides an auditable record. For complex requests, write the design **before** handing execution to Codex.

## 3. Layered instructions architecture

```mermaid
flowchart TB
    subgraph GPT["ChatGPT"]
      CG["Custom Instructions<br/>Personal, cross-conversation guidance"]
      CP["Project Instructions<br/>Tech Lead workflow and project-domain behavior"]
      CG -. "general preferences" .-> CP
    end
    subgraph CDX["Codex"]
      CA["~/.codex/AGENTS.md<br/>General coding and execution principles"]
      RA["Repository AGENTS.md<br/>Project-specific constraints"]
      CA --> RA
    end
    SO[("GitHub repositories<br/>Canonical instruction files, project docs and code")]
    SO -->|"Manually sync/copy settings"| CG
    SO -->|"Manually sync/copy settings"| CP
    SO -->|"Install or sync local global file"| CA
    SO -->|"Versioned in each code repository"| RA
    CP -->|"Read relevant repo rules via GitHub"| RA
```

**Separation of concerns:**

| Location | Owns | Does not own |
| --- | --- | --- |
| ChatGPT global Custom Instructions | Personal preferences, high-level communication style | Repository-specific schemas and test commands |
| ChatGPT Project Instructions | Tech Lead / Data Architect / Reviewer workflow | One-off implementation tasks |
| Codex global `~/.codex/AGENTS.md` | General engineering practices and verification habits | Specific business metric definitions |
| Per-project `AGENTS.md` | Actual project boundaries, authoritative docs, tests | Duplicated universal philosophy |
| GitHub Issue | A single task's design, constraints and acceptance criteria | Permanent project policy |
| GitHub PR | Implementation, test evidence, review discussion | Unreviewed production authorization |

Project-level rules in GitHub must stay with their **own code repository**. This configuration repository stores a reusable template, not a second copy of every project's rules.

## 4. Repository layout

```text
ChatGPT-with-Codex-skill/
├── README.md
├── chatgpt/
│   ├── global.md
│   └── projects/
│       └── data-development.md
├── codex/
│   └── AGENTS.md
├── templates/
│   ├── repository-AGENTS.md
│   ├── development-issue.md
│   └── pr-review.md
└── docs/
    ├── architecture.md
    └── workflow.md
```

## 5. How to use

1. Review the instructions in `chatgpt/global.md` and `chatgpt/projects/data-development.md`, then paste them into their corresponding ChatGPT settings. They **do not auto-sync**.
2. Review `codex/AGENTS.md` and install it as `~/.codex/AGENTS.md` on your Mac. Its contents should not replace a repository's own `AGENTS.md`.
3. For each coding repository, adapt `templates/repository-AGENTS.md` into that repository's `AGENTS.md`.
4. For substantial changes, create an Issue using `templates/development-issue.md`. Codex reads the Issue, implements it on a branch, tests, and opens a PR.
5. ChatGPT reviews the PR using `templates/pr-review.md`. The user decides whether to merge or deploy.

See [Architecture](docs/architecture.md) and [Workflow](docs/workflow.md) for details.

## 6. Working principles

- **ChatGPT leads the design; Codex executes the specification.**
- **GitHub retains decisions and evidence** through Issues, PRs, docs and code.
- **Instructions describe durable policy; Issues describe individual tasks.**
- **Verification is evidence-based:** never claim tests ran if they did not.
- **Cost optimization is a goal, not permission to skip safety or correctness.**
