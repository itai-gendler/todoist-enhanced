---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor picks a tag for the task or the selected tasks
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
- text: The Product adds the tag to each task and keeps its other tags
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
- kind: code
  role: implementation
  target: src/domain/dnd.ts
---

# Add task tag in the demo

## Trigger

The Visitor picks a tag for a task, or for several selected tasks. The visitor is using the disposable demo.

## Outcome

Each task carries the tag in addition to the tags it already had. Changes affect demonstration work only; no request is sent to Todoist.
