---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor chooses a day for the task
  kind: actor
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
  actor: visitor
  contexts:
    web:
      place: web::public::task
- text: The Product sets the date and removes the week label
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
      place: web::public::task
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

# Give work a day in the demo

## Trigger

The Visitor gives a task a day: Today, Tomorrow, or a date. The visitor is using the disposable demo.

## Outcome

The task is dated and loses the week label, so it appears in Today or Upcoming by its date. Changing only the day keeps an existing time and repeat rule. Changes affect demonstration work only; no request is sent to Todoist.
