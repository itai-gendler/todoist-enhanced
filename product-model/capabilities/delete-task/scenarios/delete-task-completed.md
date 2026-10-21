---
kind: alternate
routes:
  web: Connected account
steps:
- text: Delete the completed task
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
- text: Remove the completed task
  kind: product
  entities:
  - entity: task
    effect: removes
    from: Completed
  actor: user
  contexts:
    web:
      place: web::connected::task
references:
- kind: code
  role: implementation
  target: src/store/tasks.ts
---

# Delete completed work

## Trigger

The person confirms deletion of a completed task.

## Outcome

The completed task is removed through the same deletion process.
