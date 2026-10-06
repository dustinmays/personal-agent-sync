---
name: repo-structure-v1
description: Use when creating or maintaining a software repository.
version: 0.3.0
author: Hermes Agent
license: MIT
platforms: [linux, macos, windows]
metadata:
  hermes:
    tags: [repositories, prototypes, templates, scaffolding, coding, agents]
    related_skills: [project-structure-v1, test-driven-development]
---
# Repository Structure V1

Use this skill for runnable or versioned software: applications, APIs, CLIs, libraries, automations, and prototype monorepos. It is adaptable guidance, not a migration mandate for established repositories.

## Route before creating

1. **Classify the primary residue.** Runnable/versioned software belongs in a repository. Long-duration decisions, research, and outcome status belong in a project workspace. A one-off task needs neither root.
2. **Look for an existing owner.** Continue the repository that owns the deliverable; do not create a near-duplicate merely to start fresh.
3. **Apply the hybrid rule.** When a project needs software, link the project and repository lightly: the project explains why; the repository points back to the owning project or initiative. The project does not hold product code, and the repository does not duplicate outcome-level tracking.

If abandoning the work next week leaves a codebase to clone and run, it is a repository. If it leaves a body of notes and decisions, it is a project workspace.

## Select the smallest fitting route

- **Single application, service, CLI, or library:** use one focused repository with its ecosystem-appropriate layout.
- **Rapid-iteration prototype monorepo:** when one project or initiative needs several small, related experiments, use one repository with independently runnable `prototypes/<name>/` directories rather than one repository per experiment.

## Universal conventions

- Read existing `AGENTS.md`, `README.md`, and local instructions before changing a repository.
- Keep root `AGENTS.md` short: purpose, canonical commands, routing, and shared guardrails. Use short nested `AGENTS.md` files only for material local rules; do not repeat root guidance.
- A compatibility `CLAUDE.md` may point to `AGENTS.md` when useful.
- Expose one canonical command interface appropriate to the ecosystem. CI calls project commands, not ad-hoc raw invocations.
- Pin language and toolchain versions with ecosystem-appropriate files. Keep fast checks distinct from dependent browser/service/container checks.
- Use proportionate verification: focused behavior tests plus formatter/linter/build checks for simple prototypes; deeper testing when risk warrants it.
- A repository may track code-level delivery with concise `STATE.md`, append-only workstream `status.md`, and small independent `deferred/` notes. Do not duplicate parent-project lifecycle tracking.

## Rapid-iteration prototype monorepo

Use this structure when repeated experiments share project context and collaboration rules but may need separate dependencies or architecture:

```text
prototype-monorepo/
├── AGENTS.md                 # Short routing and shared guardrails
├── README.md
├── STATE.md                  # Repository-level implementation state
├── docs/                     # Shared, evidence-backed implementation lessons
├── scripts/                  # Shared helpers
├── mise.toml                 # Optional root task entry points
└── prototypes/
    ├── _template/            # Copy-only starter; not an active experiment
    └── experiment-name/
        ├── AGENTS.md         # Short local instructions
        ├── README.md
        ├── <local tooling>
        ├── src/
        ├── tests/
        ├── data/             # Synthetic/sample only
        └── docs/
```

- Keep the root at the routing/policy level: shared safe-data boundary, shared tooling, cross-prototype lessons, and concise repository state.
- Each prototype owns short local guidance, isolated dependencies, tests, sample-data policy, and scoped docs.
- Start experiments by copying `_template`; do not use the template itself as an experiment.
- Do not force shared runtime dependencies or architecture on unrelated experiments.
- Define a safe-data boundary before experiments begin. Unless explicitly approved otherwise, use synthetic or fabricated fixtures and exclude credentials, personal data, production data, and contract-sensitive artifacts.

## Creation and maintenance procedure

1. Confirm the intended repository location exists and is writable.
2. Inspect existing repositories and instructions. Choose an existing template only when it fits; otherwise create the smallest purpose-built repository.
3. For multiple related experiments, create the prototype-monorepo root and a copy-only template before adding a runnable prototype.
4. Add minimal context, canonical commands, runnable behavior, and a focused verification path before declaring a route usable.
5. Initialize local Git when appropriate. Do not create a remote, alter hosting settings, or publish unless explicitly asked.
6. Add a thin project/repository link only when both are real. Update the project at the appropriate milestone.

## Verification

Before reporting a repository route as usable, verify:

- The work belongs in a repository and any project linkage is documented.
- README, root and scoped guidance, state/history conventions, and commands agree.
- For a prototype monorepo, the root routes to a copy-only template and every runnable prototype is independently documented, tested, and bounded by the shared safe-data policy.
- The fast verification command and an appropriate smoke check actually succeed; disclose unavailable optional checks.
- Git status is clean except for intentional, reported changes.
