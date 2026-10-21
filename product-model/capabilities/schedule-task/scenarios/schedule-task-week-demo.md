---
kind: alternate
routes:
  web: Demo
steps:
- text: The Visitor chooses Anytime this week for the task
  kind: actor
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
  actor: visitor
  contexts:
    web:
      place: web::public::week
- text: The Product clears the date and adds the week label
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

# Commit work to this week in the demo

## Trigger

The Visitor commits a task to this week without giving it a day. The visitor is using the disposable demo.

## Outcome

The task is undated and carries the week label, so My week lists it under Anytime this week. Changes affect demonstration work only; no request is sent to Todoist.
