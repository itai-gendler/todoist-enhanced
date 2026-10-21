---
kind: primary
routes:
  web: Connected account
steps:
- text: The User opens Someday
  kind: actor
  entities: []
  actor: user
  contexts:
    web:
      place: web::connected::someday
- text: The Product lists the tasks with neither a date nor the week label
  kind: product
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Due date
    - Tags
    - Created on
    - Kept on
    - Estimate
    - Priority
  actor: user
  contexts:
    web:
      place: web::connected::someday
references:
- kind: code
  role: implementation
  target: src/views/SimpleListView.tsx
- kind: code
  role: implementation
  target: src/domain/views.ts
---

# Browse Someday

## Trigger

The User opens Someday.

## Outcome

Someday lists open tasks with neither a date nor the week label. When Gathering dust is on, tasks created longer ago than the chosen delay are gathered in their own group, each offering This week, Keep or Delete.

## Edge cases

- An empty selection is shown as no matching work; the product does not invent tasks.
