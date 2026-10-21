---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor reopens the completed task
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
- text: The Product returns the task to open work
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Completed on
    from: Completed
    to: Open
  actor: visitor
  contexts:
    web:
      place: web::public::task
references:
- kind: code
  role: implementation
  target: src/store/tasks.ts
---

# Reopen task in the demo

## Trigger

The Visitor reopens a completed one-off task. The visitor is using the disposable demo.

## Outcome

The task is open again in its lists. Changes affect demonstration work only; no request is sent to Todoist.
