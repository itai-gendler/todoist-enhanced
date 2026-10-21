---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor chooses Keep on the task
  kind: actor
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
  actor: visitor
  contexts:
    web:
      place: web::public::someday
- text: The Product records today as the day the task was kept, on this device
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Kept on
  actor: visitor
  contexts:
    web:
      place: web::public::someday
references:
- kind: code
  role: implementation
  target: src/store/dust.ts
- kind: code
  role: implementation
  target: src/domain/views.ts
---

# Keep in Someday in the demo

## Trigger

The Visitor chooses Keep on a task in Gathering dust. The visitor is using the disposable demo.

## Outcome

The task leaves Gathering dust and stays in Someday; it comes back only after another full delay. Changes affect demonstration work only; no request is sent to Todoist.
