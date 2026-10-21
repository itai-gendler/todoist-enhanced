---
kind: primary
routes:
  web: Connected account
steps:
- text: The User picks a tag for the task or the selected tasks
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
- kind: code
  role: implementation
  target: src/domain/dnd.ts
---

# Add task tag

## Trigger

The User picks a tag for a task, or for several selected tasks.

## Outcome

Each task carries the tag in addition to the tags it already had.
