---
name: project-structure-v1
description: Use when creating or maintaining project workspaces.
version: 0.2.0
author: Hermes Agent
license: MIT
platforms: [linux, macos, windows]
metadata:
  hermes:
    tags: [projects, workspaces, initiatives, status, agents]
    related_skills: [repo-structure-v1]
---
# Project Structure V1

Use this skill for long-duration work whose durable residue is decisions, research, coordination, and outcome status. It is adaptable guidance, not a required folder template.

## Route before creating

- Use a **project workspace** for context, discovery, decisions, initiative status, meeting material, and deferred work.
- Use a **repository** for runnable/versioned software with its own build, test, and release lifecycle.
- Use both when a long-duration project needs real software: the project explains why and tracks outcomes; the repository holds code and implementation delivery material.

## Smallest useful project shape

```text
project-workspace/
├── AGENTS.md             # Short project-wide instructions
├── README.md             # Purpose, scope, links, and starting point
├── STATE.md              # Concise lifecycle index
├── docs/                 # Reusable project decisions and references
├── initiatives/          # Only for substantial active work
│   └── initiative-name/
│       ├── docs/
│       └── status.md     # Append-only history
└── deferred/             # Small, independent deferred notes when useful
```

Create only folders that serve known work. Keep `AGENTS.md` files short, actionable, and non-duplicative. Preserve an established workspace's conventions unless a real change requires migration.

## Core practice

- Inspect existing instructions and repository state before editing. Do not overwrite user content.
- Keep `STATE.md` concise and current: group one-line entries under Active, Blocked, Dormant/Proposed, and Recently completed.
- Keep durable project-wide material in `docs/`; keep initiative-specific detail beside the initiative.
- Append meaningful initiative history to `status.md` with a truthful date/time. Do not rewrite history to conceal corrections.
- Use one small deferred note per independent item when useful; do not present deferred work as a current blocker.
- Keep one source of truth per information type: project workspace for context and lifecycle, task manager for actionable commitments, calendar for time commitments.

## Linked rapid-iteration prototype monorepos

When one project or initiative needs several related rapid experiments, link one prototype monorepo instead of creating a repository per experiment.

- The **project workspace** remains the discovery, decision, outcome-status, and initiative-history layer.
- The **monorepo** holds bounded runnable implementations in `prototypes/<name>/`; each prototype is an implementation experiment, not a second initiative workspace.
- Link both directions: project/initiative explains the reason and scope; repository points to its owner.
- Keep repository-root guidance high-level and put short local `AGENTS.md` files, dependencies, tests, synthetic/sample-data rules, and scoped docs inside each prototype.
- Keep project-level lifecycle information in the workspace; use repository status/history only for implementation details and handoffs.

## Verification

Before reporting a workspace usable, verify:

- The destination is the intended writable project location.
- README, AGENTS, and STATE agree on scope and current state.
- State entries are concise and non-duplicative; status history is append-only.
- Project-to-repository links are documented without duplicating code or outcome tracking.
- New files and links are readable and valid.
