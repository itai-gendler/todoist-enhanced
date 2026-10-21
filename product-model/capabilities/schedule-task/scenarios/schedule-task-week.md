---
kind: alternate
routes:
  web: Connected account
steps:
- text: The User chooses Anytime this week for the task
  kind: actor
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
  actor: user
  contexts:
    web:
      place: web::connected::week
- text: The Product clears the date and adds the week label
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
      place: web::connected::week
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

# Commit work to this week

## Trigger

The User commits a task to this week without giving it a day.

## Outcome

The task is undated and carries the week label, so My week lists it under Anytime this week.
