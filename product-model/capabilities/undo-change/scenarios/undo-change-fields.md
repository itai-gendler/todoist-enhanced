---
kind: primary
routes:
  web: Connected account
steps:
- text: Undo a recorded task change
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
  actor: user
  contexts:
    web:
      place: web::connected::task
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

# Undo a recorded task change

## Trigger

The person chooses Undo after a reversible task operation.

## Outcome

The captured changed fields are restored, waiting for the original request when required.
