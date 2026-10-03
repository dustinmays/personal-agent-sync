# Repository Structure V1 for an Independent Gateway

- **Status:** reviewed implementation note
- **Added:** 2026-10-03 UTC
- **Origin:** generalized from a cooperating Hermes environment
- **Applies to:** a Hermes gateway that can clone or pull this repository's reviewed remote
- **Confidence:** high for the file and review boundary; local mounts, profiles, and toolchains require independent verification

## Goal

Give a separately operated Hermes gateway the same repository-routing and maintenance guidance without sharing its memory, sessions, credentials, profile configuration, or private project context.

This repository is a **reviewed exchange layer**, not a shared Hermes home. It distributes a portable skill and explanatory documentation through normal version control. Each gateway remains responsible for its own authorization, configuration, environment-specific instructions, and local skill installation.

## What is provided

```text
personal-agent-sync/
├── AGENTS.md                         # Safety and contribution boundary
├── README.md                          # Purpose and review workflow
├── STATE.md                           # Concise lifecycle index for this exchange repo
├── docs/
│   ├── sharing-protocol.md            # Contribution and consumption protocol
│   └── repository-structure-v1-for-independent-gateway.md
└── skills/
    └── repo-structure-v1/
        └── SKILL.md                   # Portable repository-structure guidance
```

The `repo-structure-v1` skill routes runnable/versioned software to a repository, separates it from project-level context, and defines small, verifiable repository conventions. It is guidance rather than a migration mandate: an established repository keeps its own conventions unless real work calls for a change.

## Destination-gateway adoption

1. Clone or pull this reviewed repository from its approved remote on the destination VPS. No shared filesystem, mount, or access to the source gateway is required; the destination only needs ordinary Git access to the reviewed remote.
2. Read `AGENTS.md`, `README.md`, `docs/sharing-protocol.md`, and this note before trusting or copying any skill.
3. Review the diff for `skills/repo-structure-v1/SKILL.md`. Reject changes that contain secrets, raw memory, profile exports, private paths, or environment-specific instructions presented as portable rules.
4. Choose one installation scope:

   - **Repository-owned use:** from the checkout, run `hermes skills trust <checkout-path>`. This keeps the skill versioned with the repository and is appropriate when working with this trusted checkout.
   - **Gateway-global use:** after reviewing it, copy `skills/repo-structure-v1/` into the destination gateway's own `$HERMES_HOME/skills/software-development/` directory. Do not overwrite an existing local `repo-structure-v1` directory blindly; compare it first and preserve any destination-specific additions.

5. Verify the destination agent can discover the skill and load it for repository-creation or repository-maintenance work. Then run the skill's own repository checks when it is applied to a real repository.

For a new global installation only, this guarded shell sequence uses the active profile home when `HERMES_HOME` is set and otherwise uses the default home:

```bash
SYNC_REPO="/path/to/personal-agent-sync"
HERMES_HOME="${HERMES_HOME:-$HOME/.hermes}"
SOURCE="$SYNC_REPO/skills/repo-structure-v1"
TARGET="$HERMES_HOME/skills/software-development/repo-structure-v1"

test -f "$SOURCE/SKILL.md" || { echo "Portable skill not found: $SOURCE"; exit 1; }
test ! -e "$TARGET" || { echo "Refusing to overwrite existing skill: $TARGET"; exit 1; }
mkdir -p "$(dirname "$TARGET")"
cp -R "$SOURCE" "$TARGET"
```

If the destination is a named profile, ensure `HERMES_HOME` resolves to that profile's real home before copying. Do not hard-code another gateway's home path.

## How the skill should be used

The destination agent should load `repo-structure-v1` whenever it creates or maintains runnable, versioned software. The principal decisions are:

- Put software with its own build, test, version-control, or release lifecycle in a repository; put long-duration decisions, research, and outcome tracking in a project workspace.
- Prefer an existing repository when it owns the same deliverable.
- Keep a repository's `README.md`, concise root `AGENTS.md`, `STATE.md`, canonical command interface, and verification path consistent.
- Link a project and a repository only when both are real: project context says why; the repository owns code and code-level delivery material.
- Keep verification proportionate but real: run the documented fast check and a build/run smoke test before declaring a route usable.

Do not use the skill to bulk-reorganize established repositories for uniformity.

## Ongoing exchange practice

- Pull and inspect changes before using a new shared-skill revision.
- Keep local customizations in the owning gateway unless they are generalized, evidence-backed, and safe to contribute.
- Publish repeatable cross-environment procedures as skills; publish narrower evidence and limitations as learning notes.
- Do not synchronize `MEMORY.md`, user profiles, sessions, credentials, OAuth state, logs, or configuration between gateways.
- Do not enable automatic two-way writes between gateway profiles. Git review is the synchronization mechanism for this repository.

## Verification checklist

- [x] Portable skill is present at `skills/repo-structure-v1/SKILL.md`.
- [x] Installation paths use the destination gateway's own `$HERMES_HOME` rather than another gateway's path.
- [x] The guarded global-install command refuses to overwrite an existing skill.
- [x] The process preserves review, privacy, and independent-gateway boundaries.
- [x] No credentials, user-profile data, private endpoints, raw memory, or transcript excerpts are included.
