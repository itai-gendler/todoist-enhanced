---
kind: alternate
routes:
  web: Connected account
steps:
- text: Choose to remove the task date
  kind: actor
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Due date
    - Tags
  actor: user
  contexts:
    web:
      place: web::connected::issues
- text: Clear the task date
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Due date
    - Repeat rule
  actor: user
  contexts:
    web:
      place: web::connected::issues
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

# Keep the week commitment instead of a date

## Trigger

The person chooses Remove date for a task carrying both a date and the week label.

## Outcome

The due date is cleared and the week label remains, placing the task in the undated weekly commitment.
