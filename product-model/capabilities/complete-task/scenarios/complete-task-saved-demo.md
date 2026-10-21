---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor completes the task or the selected tasks
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
- text: The Product marks each one-off task completed
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Completed on
    from: Open
    to: Completed
  actor: visitor
  contexts:
    web:
      place: web::public::task
references:
- kind: code
  role: implementation
  target: src/store/tasks.ts
---

# Complete task in the demo

## Trigger

The Visitor completes a one-off task, or several selected tasks. The visitor is using the disposable demo.

## Outcome

The tasks leave the open lists and are recorded as completed; Undo brings them back. Changes affect demonstration work only; no request is sent to Todoist.
