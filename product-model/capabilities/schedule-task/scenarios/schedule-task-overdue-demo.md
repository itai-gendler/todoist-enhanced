---
kind: alternate
routes:
  web: Demo
steps:
- text: Confirm the overdue task selection
  kind: actor
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Due date
  actor: visitor
  contexts:
    web:
      place: web::public::week
- text: Reschedule the selected tasks
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Due date
    - Repeat rule
    - Tags
  actor: visitor
  contexts:
    web:
      place: web::public::week
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

# Reschedule the overdue group together in the demo

## Trigger

The person confirms Reschedule all on the visible overdue group. The visitor is using the disposable demo.

## Outcome

All affected tasks receive today’s date and lose the week label while keeping recurrence; one undo restores the changed fields. Changes affect demonstration work only; no request is sent to Todoist.
