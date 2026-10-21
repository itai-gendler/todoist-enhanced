---
kind: primary
routes:
  web: Connected account
steps:
- text: The User drops the task onto another row
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
- text: The Product saves the new task order, keeping the places of hidden tasks
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Order
  actor: user
  contexts:
    web:
      place: web::connected::task
references:
- kind: code
  role: implementation
  target: src/components/dnd/DragProvider.tsx
- kind: code
  role: implementation
  target: src/domain/dnd.ts
- kind: code
  role: implementation
  target: src/store/tasks.ts
---

# Reorder task

## Trigger

The User drops a task straight onto another row.

## Outcome

The task takes that row’s place; tasks hidden by the page’s filters keep their places relative to it.
