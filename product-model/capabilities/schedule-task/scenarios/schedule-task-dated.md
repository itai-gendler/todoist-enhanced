---
kind: primary
routes:
  web: Connected account
steps:
- text: The User chooses a day for the task
  kind: actor
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
  actor: user
  contexts:
    web:
      place: web::connected::task
- text: The Product sets the date and removes the week label
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
      place: web::connected::task
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

# Give work a day

## Trigger

The User gives a task a day: Today, Tomorrow, or a date.

## Outcome

The task is dated and loses the week label, so it appears in Today or Upcoming by its date. Changing only the day keeps an existing time and repeat rule.
