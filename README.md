# ChatGPT with Codex

**ChatGPT designs. Codex builds. GitHub connects them.**

A modular instruction kit for a **ChatGPT-led development workflow**. ChatGPT handles technical leadership and review; Codex focuses on implementation; GitHub stores persistent instructions, Issues, PRs, and review evidence.

## Roles and architecture

<table>
  <tbody>
    <tr>
      <td width="50%" valign="top">
        <h3>🧠 ChatGPT</h3>
        <p><sub>Tech Lead · Data Architect · Code Reviewer</sub></p>
        <p>Owns requirements, repository analysis, technical design, task breakdown, acceptance criteria, and PR review.</p>
      </td>
      <td width="50%" valign="top">
        <h3>💻 Codex</h3>
        <p><sub>Software Engineer · Executor</sub></p>
        <p>Implements scoped GitHub Issues and <code>AGENTS.md</code> rules, runs tests, addresses feedback, and creates PRs.</p>
      </td>
    </tr>
    <tr>
      <td colspan="2" valign="top">
        <h3>🐙 GitHub</h3>
        <p><sub>Source of Truth · Communication Channel</sub></p>
        <p>Stores instructions, project documentation, and code. Issues communicate implementation tasks; PRs, review comments, and CI results carry feedback and verification evidence.</p>
      </td>
    </tr>
  </tbody>
</table>

**User:** Defines goals and approves merges and deployments.

## Development workflow

**Simple changes:** ChatGPT may implement directly on a feature branch and open a PR for review.

**Codex handoff:** **ChatGPT designs → GitHub Issue → Codex implements & tests → GitHub PR → ChatGPT reviews → User approves.**

The [Issue-to-PR module](templates/github-issue-to-pr.md) provides reusable instructions for this handoff. It is **not automated**: ChatGPT creates the Issue in the application repository, and Codex requires an explicit kickoff and GitHub access.

## Instruction layers

**The `chatgpt/` directory stores the source text for ChatGPT's Instructions settings:**

- **`chatgpt/global.md`** → ChatGPT **Custom Instructions** (account-wide guidance).
- **`chatgpt/projects/*.md`** → **Project Settings → Instructions** for the corresponding ChatGPT Project (project-specific roles and rules).
- **`templates/*.md`** → **optional, standalone instruction modules** that you can add to or combine with a Project's Instructions as needed. They are not separate ChatGPT Projects.

These GitHub files are maintained as configuration references. **They do not automatically load or sync into ChatGPT**; copy the selected text into the appropriate settings.

| Layer | Location | Purpose |
| --- | --- | --- |
| ChatGPT global | [`chatgpt/global.md`](chatgpt/global.md) | Cross-conversation engineering principles |
| ChatGPT Project | [`chatgpt/projects/data-development.md`](chatgpt/projects/data-development.md) | Tech Lead / Architect / Reviewer responsibilities |
| **Optional ChatGPT modules** | [`templates/`](templates/) | Paste one or more independent workflow modules into Project Settings when needed |
| Codex global | [`codex/AGENTS.md`](codex/AGENTS.md) | General implementation and verification rules |
| Codex project references | [`codex/projects/`](codex/projects/) | Flat `<project-name>.md` copies of application `AGENTS.md` files |

Each **application repository's own `AGENTS.md`** remains the rule file Codex loads in that project. Files under `codex/projects/` are centrally stored reference copies, **not automatically loaded or synchronized**. A reusable [repository AGENTS.md starter](codex/repository-AGENTS-template.md) is also available.

## Repository structure

```text
ChatGPT-with-Codex-skill/
├── README.md
├── chatgpt/
│   ├── global.md
│   └── projects/
│       └── data-development.md
├── codex/
│   ├── AGENTS.md
│   ├── repository-AGENTS-template.md
│   └── projects/
│       └── trading-stats.md
└── templates/
    ├── github-issue-to-pr.md
    ├── development-issue.md
    └── pr-review.md
```

**Using the kit:** Copy `chatgpt/global.md` to ChatGPT Custom Instructions; paste a base Project instruction file and any desired `templates/*.md` modules together into ChatGPT Project Settings; install `codex/AGENTS.md` locally as `~/.codex/AGENTS.md`. None of these settings auto-sync from GitHub. Changes to project-rule copies must also be reconciled with their application's actual `AGENTS.md`.

Instructions define long-lived behavior; **GitHub Issues define individual tasks** and **PRs carry implementation and review evidence**.
