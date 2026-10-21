---
kind: primary
routes:
  web: Connected account
steps:
- text: The User completes the task or the selected tasks
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
- text: The Product marks each one-off task completed
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Completed on
    from: Open
    to: Completed
  actor: user
  contexts:
    web:
      place: web::connected::task
references:
- kind: code
  role: implementation
  target: src/store/tasks.ts
---

# Complete task

## Trigger

The User completes a one-off task, or several selected tasks.

## Outcome

The tasks leave the open lists and are recorded as completed; Undo brings them back.
