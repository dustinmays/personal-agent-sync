# Project and Repository Structure V1 for an Independent Gateway

- **Status:** reviewed implementation note
- **Added:** 2026-10-06 UTC
- **Origin:** generalized from a cooperating Hermes environment
- **Applies to:** a Hermes gateway that can clone or pull this reviewed repository
- **Confidence:** high for the portable routing model and review boundary; each gateway must verify its own paths, profiles, and tools

## Goal

Give an independently operated gateway portable guidance for choosing between project workspaces and software repositories, and for structuring a rapid-iteration prototype monorepo when one initiative needs several related experiments.

This repository is a reviewed exchange layer, not a shared Hermes home. It distributes portable skills through Git; each gateway owns its profile, memory, credentials, configuration, and local adaptations.

## What is provided

```text
skills/
├── project-structure-v1/SKILL.md   # Workspace, initiative, and project/repository boundary
└── repo-structure-v1/SKILL.md      # Runnable software and prototype-monorepo guidance
```

The two skills are complementary:

- `project-structure-v1` routes long-duration context, discovery, decisions, and outcome tracking to a project workspace.
- `repo-structure-v1` routes runnable/versioned software to a repository.
- When a project needs several related rapid experiments, the workspace remains the context/outcome layer and one linked prototype monorepo holds independently runnable implementations.

## Destination-gateway adoption

1. Pull this repository on the destination gateway and inspect the diff.
2. Read `AGENTS.md`, `README.md`, and `docs/sharing-protocol.md` before adopting a shared skill.
3. Review both skill files. Reject content containing private paths, credentials, raw memory, profiles, transcripts, private URLs, or environment-specific rules presented as portable guidance.
4. Either use the reviewed checkout as a repository-owned trusted skill source or copy each skill into the destination gateway's own skill directory. Do not overwrite an existing local skill blindly; compare and preserve local additions.
5. Verify the destination agent can discover and load both skills before applying them to real work.

For a new global installation, adapt the category paths to the destination's local skill layout:

```bash
SYNC_REPO="/path/to/personal-agent-sync"
HERMES_HOME="${HERMES_HOME:-$HOME/.hermes}"

PROJECT_SOURCE="$SYNC_REPO/skills/project-structure-v1"
PROJECT_TARGET="$HERMES_HOME/skills/project-structure-v1"
REPO_SOURCE="$SYNC_REPO/skills/repo-structure-v1"
REPO_TARGET="$HERMES_HOME/skills/software-development/repo-structure-v1"

for source in "$PROJECT_SOURCE" "$REPO_SOURCE"; do
  test -f "$source/SKILL.md" || { echo "Missing portable skill: $source"; exit 1; }
done
for target in "$PROJECT_TARGET" "$REPO_TARGET"; do
  test ! -e "$target" || { echo "Refusing to overwrite existing skill: $target"; exit 1; }
done

mkdir -p "$(dirname "$PROJECT_TARGET")" "$(dirname "$REPO_TARGET")"
cp -R "$PROJECT_SOURCE" "$PROJECT_TARGET"
cp -R "$REPO_SOURCE" "$REPO_TARGET"
```

## Operating model

Use a project workspace when the durable value is the evidence, decisions, initiative history, and outcome status. Use a repository when the durable value is runnable code.

For multiple related experiments, use one linked prototype monorepo rather than repeatedly cloning an all-purpose starter. Keep its root short and shared; each `prototypes/<name>/` directory owns its local instructions, dependencies, tests, and synthetic/sample data rules. Begin from a copy-only `_template` directory. Do not turn the template into an active experiment.

The project workspace links to the monorepo and retains project-level state. The monorepo links back to its owning project or initiative and retains code-level implementation status. Keep the two layers complementary, not duplicated.

## Verification checklist

- [x] Portable project and repository skills are present.
- [x] The guidance separates project context from runnable software.
- [x] The rapid-iteration monorepo pattern is generalized and contains no private project details.
- [x] Installation refuses to overwrite existing destination skills.
- [x] No credentials, profile data, raw memory, private endpoints, or transcript excerpts are included.
