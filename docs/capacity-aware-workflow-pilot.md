# Capacity-Aware Task-System Pilot

- **Status:** reviewed operating note
- **Added:** 2026-10-01
- **Origin:** both environments; generalized
- **Applies to:** a calendar, Todoist or an equivalent task manager, Project Structure V1 workspaces, and cooperating Hermes agents
- **Confidence:** medium — the model is deliberate and documented; sustainable use is still being tested

## Purpose

This is a small productivity-system pilot for a person who benefits from low-friction capture, non-linear initiative context, and planning from real calendar capacity. It is not a request to build a comprehensive task-management framework.

The system should repeatedly answer only:

1. What needs attention now?
2. Where does it belong?
3. What will remind the person later?

Any taxonomy, dashboard, filter, or automation must earn its place through repeated real use.

## System boundaries

| System | Canonical role |
|---|---|
| Calendar | Fixed commitments, real deadlines, and capacity constraints |
| Task manager | Capture Inbox, current actions, follow-ups, waiting items, and revisit ticklers |
| Project Structure V1 workspace | Initiative purpose, decisions, scoped instructions, lifecycle state, and status history |
| Hermes agents | Capture assistance, calendar-aware planning, review, and proposed reconciliation |

Do not create automatic two-way synchronization. Each system owns its kind of information.

## Task-manager model

Use two shallow navigation parents, normally with no direct tasks:

```text
Personal
├── <ongoing personal area, if it earns its place>
└── <active personal initiative>

Work
├── <ongoing work area, if it earns its place>
└── <active work initiative>
```

- **Parent project:** personal/work navigation boundary.
- **Area project:** ongoing responsibility with recurring operational work.
- **Initiative project:** a temporary outcome requiring multiple real moves.
- **Section:** a meaningful initiative workstream—not a generic workflow state.
- **Task:** a concrete next move, follow-up, or discrete commitment.
- **Subtask:** a small checklist; promote it if it needs a separate reminder, context, or owner.

Use a task-manager project only for active multi-step work or a real ongoing area. Do not migrate historical backlogs or create projects for dormant ideas.

## Anti-complexity constraints

- Do **not** use labels for project organization, work/personal categorization, or duplicate hierarchy.
- Do **not** create universal GTD-style Now/Next/Someday/Waiting sections.
- Use labels only for action-oriented context that the project path cannot express. A likely first label is `@waiting`.
- Every waiting task needs a revisit or follow-up date.
- Add labels such as `@call`, `@errand`, `@quick`, or energy-mode labels only after their value is demonstrated repeatedly.
- Use due dates for actual deadlines, follow-ups, and intentional ticklers—not estimates.
- Calendar is the capacity constraint; the task manager is candidate work.

## Agent behavior

1. Capture unstructured requests in the task Inbox only when asked; do not force a project, label, or due date at capture.
2. Before proposing a plan, read relevant initiative context, current task actions, and calendar commitments. Propose a small capacity-aware plan.
3. Keep durable decisions and history in the workspace; put only actionable commitments and ticklers in the task manager.
4. For waiting/follow-up work, make the next contact or review explicit. Apply `@waiting` only when it is useful.
5. Treat task-manager and calendar access as environment-local. Each Hermes agent must establish and verify its own authorization; never share credentials or assume a container token is accessible elsewhere.
6. Do not silently mutate external task/calendar records. Make writes only with the user's explicit authorization, then read back the changed record.
7. Do not build automatic reconciliation. A read-only drift-review experiment may report probable mismatches—an active initiative with no next action, a stale waiting item, or an orphaned task project—and draft changes for approval. Its portable contract is in [Read-Only Project Drift Review V1](read-only-project-drift-review-v1.md).

## Trial evaluation

Evaluate the system by sustainable behavior, not feature coverage:

- Is capture easy in the moment?
- Does the person return to the task manager without avoidance?
- Does calendar-first planning make tasks feel possible rather than constraining?
- Is initiative context easy to recover from the workspace?
- Do waiting/revisit dates keep contingent work visible?
- Does agent assistance reduce administration rather than add it?

## Limits / local adaptation

This is an operating model, not a verified universal method. Local workspace paths, calendar providers, task-manager authorization, and the exact project names must be configured independently in each environment. Do not add personal identifiers, credentials, account details, raw session material, or work-confidential content to this repository.

## Sharing review

- [x] No credentials, personal data, confidential work/customer details, private URLs, or raw transcript excerpts
- [x] Generalized enough to be useful outside the source environment
- [x] Scope, limits, and trial status are clear
