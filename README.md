# Personal Agent Sync

A small, reviewed exchange for reusable learnings between Dustin's personal Hermes and hermes-work. Each agent keeps its own profile, memory, sessions, credentials, and environment-specific instructions; this repository contains only material deliberately approved for sharing.

## Sharing rule

Share **general methods, verified tool behavior, and portable skills**—not transcripts or raw memory. Before adding anything learned at work, remove customer, employer, project, and other confidential details. Treat this repository as public-facing unless its GitHub visibility has been independently confirmed otherwise. Never put credentials, tokens, private URLs, or personal data here.

## What belongs here

- `learnings/`: concise, reviewed notes with evidence and limits.
- `skills/`: portable Hermes skills ready for a human to review and copy/install into an agent.
- `docs/sharing-protocol.md`: how to propose, review, and consume learnings.
- `docs/repository-structure-v1-for-independent-gateway.md`: how a separate gateway can receive and use the portable repository-structure skill.
- `templates/learning.md`: starting format for a learning note.

Do not add `MEMORY.md`, `USER.md`, session exports, logs, or profile backups. This is not a shared Hermes home and does not automatically sync either agent's memory.

## Workflow

1. Ask the agent that learned something to draft a generalized note or skill, using the template and removing sensitive specifics.
2. Review the facts, evidence, applicability, and sharing safety yourself.
3. Commit the approved change to this repository; use a pull request if that better fits the review.
4. The other agent can read the note or copy a skill into its own profile after review. Keep local adaptations in that agent's environment, not in shared memory.

See [the sharing protocol](docs/sharing-protocol.md) for details. This v1 is intentionally manual: no credentials, automatic memory provider, or cross-environment write automation is configured.
