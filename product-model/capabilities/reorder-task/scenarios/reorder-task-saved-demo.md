---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor drops the task onto another row
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
- text: The Product saves the new task order, keeping the places of hidden tasks
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Order
  actor: visitor
  contexts:
    web:
      place: web::public::task
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

# Reorder task in the demo

## Trigger

The Visitor drops a task straight onto another row. The visitor is using the disposable demo.

## Outcome

The task takes that row’s place; tasks hidden by the page’s filters keep their places relative to it. Changes affect demonstration work only; no request is sent to Todoist.
