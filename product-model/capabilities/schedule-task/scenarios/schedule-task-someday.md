---
kind: alternate
routes:
  web: Connected account
steps:
- text: The User chooses Someday for the task
  kind: actor
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
  actor: user
  contexts:
    web:
      place: web::connected::someday
- text: The Product clears the date and removes the week label
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
      place: web::connected::someday
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

# Return work to Someday

## Trigger

The User sends a task to Someday.

## Outcome

The task has neither a date nor the week label and is listed in Someday.
