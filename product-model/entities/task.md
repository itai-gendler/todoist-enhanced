---
references:
- kind: code
  role: implementation
  target: src/domain/types.ts
relations:
- entity: task
  verb: contains
  cardinality: one-to-many
- entity: comment
  verb: has
  cardinality: one-to-many
---

# Task

A piece of work held in Todoist, or a disposable demo task. Subtasks are tasks with a parent. Checklists are part of the description, not separate tasks.

## Information kept

- **Title** — The task name; an initial * followed by a space marks an uncompletable task.
- **Description** — Markdown text, including any checklist lines and their checked marks.
- **Priority** — P1 through P4, with P1 the highest.
- **Due date** — An optional day and time.
- **Repeat rule** — An optional repeating schedule sent to Todoist for its authoritative result.
- **Deadline** — An optional date distinct from the scheduled day.
- **Tags** — Named labels attached to the task, including technical planning labels.
- **Estimate** — Positive estimated minutes, read from the selected source with fallback to the other.
- **Native duration** — The optional Todoist duration; only positive minute durations count as estimates.
- **Project** — The project holding the task.
- **Section** — An optional section in that project.
- **Parent** — An optional parent task.
- **Assignee** — An optional person from the project.
- **Order** — The task position among siblings or across a dated list.
- **Created on** — The creation time supplied for the task.
- **Completed on** — The completion time when available.
- **Kept on** — The local day the person last deliberately kept this task in Someday.
- **Completable** — Whether the title lacks the uncompletable marker.

## States

### Open

Work that has not been completed.

### Completed

A completed task that can be inspected and, for a one-off task, reopened.
