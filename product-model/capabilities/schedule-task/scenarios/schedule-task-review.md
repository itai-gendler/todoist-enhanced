---
kind: alternate
routes:
  web: Connected account
steps:
- text: The User chooses Today, Tomorrow, Anytime this week or Someday for the task
  kind: actor
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
  actor: user
  contexts:
    web:
      place: web::connected::review
- text: The Product applies that commitment to the task without leaving the review
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Due date
    - Repeat rule
    - Tags
  actor: user
  contexts:
    web:
      place: web::connected::review
references:
- kind: code
  role: implementation
  target: src/domain/dnd.ts
- kind: code
  role: implementation
  target: src/store/tasks-move.ts
- kind: code
  role: implementation
  target: src/views/WeekView.tsx
- kind: code
  role: implementation
  target: src/store/calendar.ts
---

# Reschedule from the review

## Trigger

A review step shows a task that needs a commitment.

## Outcome

The task takes the chosen commitment at once, and the review stays on its step.
