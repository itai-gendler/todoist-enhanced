---
kind: alternate
routes:
  web: Demo
steps:
- text: The Visitor chooses Someday for the task
  kind: actor
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
  actor: visitor
  contexts:
    web:
      place: web::public::someday
- text: The Product clears the date and removes the week label
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
      place: web::public::someday
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

# Return work to Someday in the demo

## Trigger

The Visitor sends a task to Someday. The visitor is using the disposable demo.

## Outcome

The task has neither a date nor the week label and is listed in Someday. Changes affect demonstration work only; no request is sent to Todoist.
