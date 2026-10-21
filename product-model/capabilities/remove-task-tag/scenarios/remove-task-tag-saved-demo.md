---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor removes a tag from the task or the selected tasks
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
  actor: visitor
  contexts:
    web:
      place: web::public::task
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
  actor: visitor
  contexts:
    web:
      place: web::public::task
references:
- kind: code
  role: implementation
  target: src/components/BulkBar.tsx
- kind: code
  role: implementation
  target: src/components/overlays/TaskDetail.tsx
---

# Remove task tag in the demo

## Trigger

The Visitor takes a tag off a task, or off several selected tasks. The visitor is using the disposable demo.

## Outcome

The tag is gone from each task; its other tags remain. Changes affect demonstration work only; no request is sent to Todoist.
