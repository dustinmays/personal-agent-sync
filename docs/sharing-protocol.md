# Sharing protocol

## Boundary

Each Hermes instance remains the source of truth for its own memory, user profile, sessions, credentials, and machine-specific setup. This repository is a curated exchange layer—not a mirror and not a synchronization mechanism.

Treat the repository as public-facing unless visibility has been explicitly verified. Do not share employer/customer confidential information, personal identifiers, credentials, private endpoints, raw conversation text, memory files, logs, or profile exports. If a lesson cannot be safely generalized, keep it local.

## Contribute

1. Identify a lesson likely to help the other agent beyond the current task.
2. Ask the source agent to draft a short, self-contained learning note or portable Hermes skill. Do not let it copy the whole session or memory.
3. Remove identifying or sensitive details. Replace environment-specific values with placeholders and call out anything that must be adapted locally.
4. Record what was observed, how it was checked, where it applies, and known limitations. Distinguish observed facts from hypotheses.
5. Review the diff yourself. Reject stale, unsubstantiated, duplicated, or unsafe content.
6. Commit the approved change. Use a pull request when additional review is useful; otherwise a reviewed local commit is sufficient.

Use `../templates/learning.md` for standalone findings. Put a repeatable, cross-environment procedure in `skills/<skill-name>/SKILL.md`, following the standard Hermes skill format and keeping environment-specific setup out of the portable skill.

## Consume

1. Fetch or pull the repository in the destination environment; inspect the diff before updating if local edits exist.
2. Read applicable learning notes when relevant.
3. Review a skill before copying/installing it into that agent's own skill directory. Adapt or supplement machine-specific details locally.
4. Keep personal/work preferences and environment facts in the owning agent's own memory. Do not copy this repository wholesale into `MEMORY.md`.

## Concurrent edits

Avoid editing the same files from both environments concurrently. Pull before starting, make a focused change, and resolve any conflict deliberately. Do not set up automatic two-way sync until the review and privacy boundary is working well manually.
