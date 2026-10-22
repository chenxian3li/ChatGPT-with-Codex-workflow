# Project AGENTS.md registry

This directory groups copies of the `AGENTS.md` files used by active development repositories.

## Convention

Use one subdirectory per project, named after its repository:

```text
projects/
├── README.md
└── trading-stats/
    └── AGENTS.md
```

Add more repositories here only when they are actively in scope. If two repositories have the same short name, use an owner-qualified directory name.

## Source of truth and synchronization

- The `AGENTS.md` **in the actual application repository** is the effective version Codex reads during local development.
- This directory preserves a **central reference copy** for discoverability and review. It does not automatically inject rules into other repositories.
- When either copy changes, compare and reconcile the two. Changes here must also be carried to the application's own `AGENTS.md` before Codex will follow them there.
- For task planning, prefer reading the live application's `AGENTS.md` rather than assuming this snapshot is current.
- Never store credentials or sensitive configuration in these files.

The reusable starting template remains [`templates/repository-AGENTS.md`](../templates/repository-AGENTS.md). A template is not a substitute for a project's actual rules.
