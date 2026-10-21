---
kind: primary
routes:
  web: Demo
steps:
- text: Undo a recorded task change
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
- text: Restore the affected task fields
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Due date
    - Tags
    - Priority
    - Project
    - Section
    - Parent
    - Order
  actor: visitor
  contexts:
    web:
      place: web::public::task
references:
- kind: code
  role: implementation
  target: src/store/ui.ts
- kind: code
  role: implementation
  target: src/store/tasks.ts
- kind: code
  role: implementation
  target: src/store/tasks-move.ts
---

# Undo a recorded task change in the demo

## Trigger

The person chooses Undo after a reversible task operation. The visitor is using the disposable demo.

## Outcome

The captured changed fields are restored, waiting for the original request when required. Changes affect demonstration work only; no request is sent to Todoist.
