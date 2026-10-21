---
kind: primary
routes:
  web: Connected account
steps:
- text: The User opens My week
  kind: actor
  entities: []
  actor: user
  contexts:
    web:
      place: web::connected::week
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
  actor: user
  contexts:
    web:
      place: web::connected::week
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

# Browse My week

## Trigger

The User opens My week.

## Outcome

My week shows Behind schedule, Quick, today without a time, today with a time, then Anytime this week, with a load line against the weekly capacity. A task dated later this week is in Upcoming, not here.

## Edge cases

- An empty selection is shown as no matching work; the product does not invent tasks.
