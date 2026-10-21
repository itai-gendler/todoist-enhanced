---
kind: edge
routes:
  web: Connected account
steps:
- text: Open the completed task
  kind: actor
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Completed on
  actor: user
  contexts:
    web:
      place: web::connected::task
- text: Try to retrieve the task and show the available record
  kind: product
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Completed on
  - entity: comment
    effect: reads
    facts:
    - Text
  actor: user
  contexts:
    web:
      place: web::connected::task
references:
- kind: code
  role: implementation
  target: src/components/overlays/TaskDetail.tsx
- kind: code
  role: implementation
  target: src/store/tasks.ts
---

# Open an unavailable history entry

## Trigger

The user opens a completed entry whose full task is not cached.

## Outcome

The app fetches the task and comments when possible, or shows its unavailable/offline state with the available completion summary.
