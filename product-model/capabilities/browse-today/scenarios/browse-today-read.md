---
kind: primary
routes:
  web: Connected account
steps:
- text: The User opens Today
  kind: actor
  entities: []
  actor: user
  contexts:
    web:
      place: web::connected::today
- text: The Product lists overdue tasks and tasks due today against today’s capacity
  kind: product
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Due date
    - Tags
    - Estimate
    - Priority
    - Assignee
  - entity: settings
    effect: reads
    facts:
    - Daily capacity
  actor: user
  contexts:
    web:
      place: web::connected::today
references:
- kind: code
  role: implementation
  target: src/views/WeekView.tsx
- kind: code
  role: implementation
  target: src/domain/load.ts
---

# Browse Today

## Trigger

The User opens Today.

## Outcome

Today lists what is overdue and what is due today, with a load line comparing their estimates with that weekday’s capacity.

## Edge cases

- An empty selection is shown as no matching work; the product does not invent tasks.
