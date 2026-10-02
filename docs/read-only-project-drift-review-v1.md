# Read-Only Project Drift Review V1

- **Status:** reviewed operating experiment
- **Added:** 2026-10-02
- **Origin:** both environments; generalized
- **Applies to:** a task manager, Project Structure V1 workspaces, and two or more Hermes gateways sharing a task store
- **Confidence:** medium — boundaries are deliberate; report usefulness is still unproven

## Purpose

Use a small, agent-assisted review to spot meaningful differences between a task manager's active commitments and a gateway's accessible project context. This is **not** two-way synchronization.

- The **task manager** owns concrete actions, dates, and follow-up ticklers.
- The **workspace or repository** owns initiative purpose, decisions, lifecycle context, and history.
- A **Hermes gateway** reads both sources in its own scope and proposes a few decisions.

The goal is reliable orientation, not a complete inventory or another task-management system.

## Separate the two reviews

### Project drift review

A gateway compares active project context it can actually read with the task-manager projects and tasks assigned to that same scope.

It may report only material signals:

1. An active initiative needs near-term work but has no corresponding task-manager project or concrete next action.
2. An active task-manager project has no identifiable current project context.
3. One source says the work is materially blocked, complete, or dormant while the other still presents conflicting active commitments.
4. A blocked/waiting task lacks an explicit follow-up or review date.

A report requests review; it never decides automatically which source is correct.

### Today and Inbox triage

Today/Inbox review is separate. The Inbox is intentional low-friction capture, not evidence of drift.

One-off tasks may remain standalone. An Inbox review can propose that the user keep an item standalone, attach it to an existing project, add a date, promote it to an initiative if it truly grew, or discard it with explicit approval. It must not force every item into a project or general-purpose tag scheme.

An always-available personal gateway is a good owner for recurring Today/Inbox orientation. A work gateway should own only the work context it can read.

## Read-only contract

A first drift-review experiment must:

1. Read explicit active workspace/project indexes plus only the relevant scoped status material.
2. Read task-manager projects and active tasks in the agreed review scope.
3. Compare only mapped initiatives and project-linked tasks.
4. Return no more than three discrepancies, in practical-impact order.
5. Say `No material drift found` when applicable.
6. Give one concrete proposed decision or next action for each discrepancy.

It must not, without a separate explicit user action:

- create, move, complete, delete, or re-date task-manager records;
- edit project state/history files;
- classify Inbox items or infer a personal/work boundary;
- synchronize one source into the other;
- treat a prior agent conversation or agent memory as an authoritative source.

## Mapping is deliberately small

Start with active, multi-step initiatives only. For each one, maintain or be able to determine:

| Field | Portable example |
|---|---|
| Context location | `<workspace>/initiatives/<initiative>` |
| Task-manager project | `<parent>/<active initiative>` |
| Lifecycle source | a project index or scoped status note |
| Review owner | personal gateway or work gateway |

Do not bulk-map historical work, dormant ideas, or every Inbox item. A missing mapping is a review question, not automatically an error.

## Scheduling experiment

A recurring report is useful only after one manual read-only comparison shows that its output is short and actionable.

Start with one workday check or a gateway-start catch-up, then evaluate it for one week:

- Did it surface a real discrepancy early enough to help?
- Was it short enough to read without avoidance?
- Did it avoid false alarms for standalone tasks, Inbox capture, dormant work, and known external blocks?
- Did it clarify a next action without creating administration?

A local cron schedule is not a guaranteed wall-clock reminder when its host or gateway is offline. Use the task manager or calendar for the reliable attention cue. A scheduled Hermes run should provide the read-only review when its gateway is available.

## Local adaptation and limits

Each gateway must have its own task-manager authorization and access to the project context it reviews. Do not share credentials or assume one gateway can read another's files. Scheduled runs begin in fresh sessions, so the job prompt must name its source paths and task-manager scope instead of relying on an earlier chat.

Container-local clients and OAuth state may disappear when containers are recreated. In that case, report task-manager access as unavailable; do not produce a guessed drift report.

## Evidence / verification

This operating contract derives from the capacity-aware task-system pilot, which established separate sources of truth for calendar, task manager, project workspaces, and agents. Hermes cron documentation confirms that scheduled jobs run in fresh sessions and depend on a running gateway; both claims are reflected as constraints rather than assumed away.

No automated drift report has been run yet. The first manual comparison is the required proof point before adding scheduled automation or application code.

## Sharing review

- [x] No credentials, personal data, confidential work/customer details, private URLs, or raw transcript excerpts
- [x] Generalized enough to be useful outside the source environment
- [x] Scope, evidence, limits, and the unproven parts are clear
