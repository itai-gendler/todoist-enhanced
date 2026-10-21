---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor opens Today
  kind: actor
  entities: []
  actor: visitor
  contexts:
    web:
      place: web::public::today
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
  actor: visitor
  contexts:
    web:
      place: web::public::today
references:
- kind: code
  role: implementation
  target: src/views/WeekView.tsx
- kind: code
  role: implementation
  target: src/domain/load.ts
---

# Browse Today in the demo

## Trigger

The Visitor opens Today. The visitor is using the disposable demo.

## Outcome

Today lists what is overdue and what is due today, with a load line comparing their estimates with that weekday’s capacity.

## Edge cases

- An empty selection is shown as no matching work; the product does not invent tasks.
