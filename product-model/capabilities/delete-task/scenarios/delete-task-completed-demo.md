---
kind: alternate
routes:
  web: Demo
steps:
- text: Delete the completed task
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
- text: Remove the completed task
  kind: product
  entities:
  - entity: task
    effect: removes
    from: Completed
  actor: visitor
  contexts:
    web:
      place: web::public::task
references:
- kind: code
  role: implementation
  target: src/store/tasks.ts
---

# Delete completed work in the demo

## Trigger

The person confirms deletion of a completed task. The visitor is using the disposable demo.

## Outcome

The completed task is removed through the same deletion process. Changes affect demonstration work only; no request is sent to Todoist.
