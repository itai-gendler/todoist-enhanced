---
kind: primary
routes:
  web: Connected account
steps:
- text: The User removes a tag from the task or the selected tasks
  kind: actor
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
  - entity: tag
    effect: reads
    facts:
    - Name
  actor: user
  contexts:
    web:
      place: web::connected::task
- text: The Product removes that tag and keeps the other tags
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Tags
  - entity: tag
    effect: reads
    facts:
    - Name
  actor: user
  contexts:
    web:
      place: web::connected::task
references:
- kind: code
  role: implementation
  target: src/components/BulkBar.tsx
- kind: code
  role: implementation
  target: src/components/overlays/TaskDetail.tsx
---

# Remove task tag

## Trigger

The User takes a tag off a task, or off several selected tasks.

## Outcome

The tag is gone from each task; its other tags remain.
