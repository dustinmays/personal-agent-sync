---
name: repo-structure-v1
description: Use when creating or maintaining a software repository.
version: 0.2.0
author: Dustin Mays, Hermes Agent
license: MIT
platforms: [linux, macos, windows]
metadata:
  hermes:
    tags: [repositories, templates, scaffolding, coding, agents, delivery]
    related_skills: [project-structure-v1, test-driven-development]
---
# Repository Structure V1

Use this skill for runnable or versioned software: applications, APIs, CLIs, TUIs, libraries, and automations with their own build, test, version-control, or release lifecycle. It is adaptable guidance, not a mandatory scaffold or a reason to reorganize an established repository.

## Route before creating

1. **Classify the primary residue.** Runnable/versioned software belongs in a repository. Long-duration work whose durable residue is decisions, research, or status belongs in a project workspace. A one-off task needs neither root.
2. **Look for an existing owner.** Continue an existing repository when it owns the same deliverable. Do not create a near-duplicate merely to start fresh.
3. **Apply the hybrid rule.** When a project needs real software, use a separate repository and link them lightly: the project explains why; the repository points to its owning project or initiative. Project context does not hold product code, and the repository does not duplicate outcome-level tracking.

Shortcut: if abandoning the work next week leaves a codebase to clone and run, it is a repository. If it leaves a body of notes and decisions, it is a project.

## Smallest useful repository shape

Start with the repository's existing `AGENTS.md`, `README.md`, and local instructions. Preserve its conventions. A new or newly structured repository normally needs only:

```text
repository/
├── AGENTS.md             # Short purpose, canonical commands, map to deeper context
├── README.md             # Purpose, setup, run/verify instructions, links
├── STATE.md              # Concise current lifecycle index when sustained work warrants it
├── <source and tests>    # Language/framework-specific layout
└── <canonical commands>  # Package scripts, Makefile targets, or equivalent
```

Add nested `AGENTS.md` files only where folder-specific rules materially help. Add a workstream status log or `deferred/` notes only for sustained implementation work. Avoid empty folders, speculative initiatives, and generic everything-templates.

## Universal conventions

- Keep root `AGENTS.md` minimal and actionable. A compatibility `CLAUDE.md` may point to it; do not rewrite a repository just for uniformity.
- Expose one canonical command interface appropriate to the ecosystem. CI calls project commands rather than hand-written raw invocations.
- Pin language and toolchain versions with ecosystem-appropriate files.
- Distinguish fast local checks from browser, service, container, or other dependent checks. Name unavailable checks explicitly; never hide a red test behind a green aggregate command.
- Keep templates thin: include a working tracer behavior, a focused behavior test or conformance check, and a documented replacement boundary.
- Use proportionate verification. Simple or non-production work benefits from focused behavior checks plus build/lint/static checks; exhaustive TDD loops are reserved for higher-risk or more complex change.
- If a repository tracks its own delivery lifecycle, use `STATE.md` as a concise current index, append-only workstream `status.md` files for history, and one small note per independent deferred item. Do not duplicate parent-project outcome tracking.

## Creation and maintenance procedure

1. Confirm the intended repository location exists and is writable. Do not create it in a project workspace or an unmounted lookalike path.
2. Inspect existing repositories and local guidance. Choose an existing template only when it fits; otherwise create the smallest purpose-built repository and record why.
3. Add the minimal repository context, canonical commands, runnable behavior, and focused verification path before declaring the route usable.
4. Initialize local Git when appropriate. Do not create a remote, alter hosting settings, or publish unless the user explicitly asks.
5. When linked to a project, add only a thin bidirectional link and update the project's initiative status at the appropriate milestone.
6. Before reporting completion, run the canonical fast check plus a suitable build/run smoke test. Report unavailable optional tooling or checks plainly.

## Portable gateway handoff

When another independently operated Hermes gateway needs this guidance, distribute a reviewed portable copy instead of copying profiles or memory.

- Publish the skill as `skills/repo-structure-v1/SKILL.md` in a reviewed exchange repository, with a companion implementation note in `docs/`.
- Keep the copy generalized. Never include raw memory, user profiles, transcripts, credentials, private endpoints, private repository URLs, or environment-local paths.
- The receiving gateway pulls and reviews the diff, then either trusts the repository-owned skill with `hermes skills trust <repo-path>` or copies the reviewed directory into its own `$HERMES_HOME/skills/` tree. Local adaptations remain local unless they later meet the sharing boundary.
- Do not create automatic two-way profile or memory synchronization. Version control and deliberate review are the exchange mechanism.

## Verification

Before reporting a repository route as usable, verify:

- The work belongs in a repository and any project linkage is documented.
- README, root guidance, state/history conventions, and canonical commands agree.
- The minimal runnable behavior can be built or run in the available environment.
- The fast verification command actually succeeds, and any unavailable optional checks are disclosed.
- Git status is clean except for intentional, reported changes.
