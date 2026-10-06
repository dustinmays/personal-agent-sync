# Personal Agent Sync

A small, reviewed exchange for reusable learnings between separate Hermes environments. Each agent keeps its own profile, memory, sessions, credentials, and environment-specific instructions; this repository contains only material deliberately approved for sharing.

## Sharing rule

Share **general methods, verified tool behavior, and portable skills**—not transcripts or raw memory. Before adding anything learned at work, remove customer, employer, project, and other confidential details. Treat this repository as public-facing unless its visibility has been independently confirmed. Never put credentials, tokens, private URLs, or personal data here.

## What belongs here

- `learnings/`: concise, reviewed notes with evidence and limits.
- `skills/`: portable Hermes skills ready for review and local installation.
- `skills/project-structure-v1/`: project workspace and project/repository boundary guidance.
- `skills/repo-structure-v1/`: software repository and rapid-iteration prototype-monorepo guidance.
- `docs/sharing-protocol.md`: how to propose, review, and consume learnings.
- `docs/project-and-repository-structure-v1-for-independent-gateway.md`: independent-gateway adoption of the paired structure skills.
- `templates/learning.md`: starting format for a learning note.

Do not add `MEMORY.md`, `USER.md`, session exports, logs, or profile backups. This is not a shared Hermes home and does not automatically synchronize either agent's memory.

## Workflow

1. Ask the agent that learned something to draft a generalized note or skill, removing sensitive specifics.
2. Review facts, evidence, applicability, and sharing safety.
3. Commit the approved change; use a pull request when useful.
4. The other agent can read a note or install a reviewed skill into its own profile. Keep local adaptations in that gateway, not shared memory.

See [the sharing protocol](docs/sharing-protocol.md) for details. This v1 is intentionally manual: no credentials, automatic memory provider, or cross-environment write automation is configured.
