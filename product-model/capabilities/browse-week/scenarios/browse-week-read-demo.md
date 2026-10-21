---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor opens My week
  kind: actor
  entities: []
  actor: visitor
  contexts:
    web:
      place: web::public::week
- text: The Product lists overdue tasks, today’s tasks and undated tasks carrying the week label, with the week’s load
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
    - Project
    - Section
    - Parent
    - Assignee
  - entity: settings
    effect: reads
    facts:
    - Daily capacity
    - Weekly override
  actor: visitor
  contexts:
    web:
      place: web::public::week
references:
- kind: code
  role: implementation
  target: src/views/WeekView.tsx
- kind: code
  role: implementation
  target: src/domain/views.ts
- kind: code
  role: implementation
  target: src/domain/load.ts
- kind: code
  role: implementation
  target: src/store/selectors.ts
---

# Browse My week in the demo

## Trigger

The Visitor opens My week. The visitor is using the disposable demo.

## Outcome

My week shows Behind schedule, Quick, today without a time, today with a time, then Anytime this week, with a load line against the weekly capacity. A task dated later this week is in Upcoming, not here.

## Edge cases

- An empty selection is shown as no matching work; the product does not invent tasks.
