---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor opens Someday
  kind: actor
  entities: []
  actor: visitor
  contexts:
    web:
      place: web::public::someday
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
  actor: visitor
  contexts:
    web:
      place: web::public::someday
references:
- kind: code
  role: implementation
  target: src/views/SimpleListView.tsx
- kind: code
  role: implementation
  target: src/domain/views.ts
---

# Browse Someday in the demo

## Trigger

The Visitor opens Someday. The visitor is using the disposable demo.

## Outcome

Someday lists open tasks with neither a date nor the week label. When Gathering dust is on, tasks created longer ago than the chosen delay are gathered in their own group, each offering This week, Keep or Delete.

## Edge cases

- An empty selection is shown as no matching work; the product does not invent tasks.
