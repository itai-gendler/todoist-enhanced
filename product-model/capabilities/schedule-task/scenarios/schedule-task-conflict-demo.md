---
kind: alternate
routes:
  web: Demo
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
  actor: visitor
  contexts:
    web:
      place: web::public::issues
- text: Clear the task date
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Due date
    - Repeat rule
  actor: visitor
  contexts:
    web:
      place: web::public::issues
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

# Keep the week commitment instead of a date in the demo

## Trigger

The person chooses Remove date for a task carrying both a date and the week label. The visitor is using the disposable demo.

## Outcome

The due date is cleared and the week label remains, placing the task in the undated weekly commitment. Changes affect demonstration work only; no request is sent to Todoist.
