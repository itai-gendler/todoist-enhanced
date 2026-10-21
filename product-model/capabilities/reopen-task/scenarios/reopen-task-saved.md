---
kind: primary
routes:
  web: Connected account
steps:
- text: The User reopens the completed task
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
- text: The Product returns the task to open work
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Completed on
    from: Completed
    to: Open
  actor: user
  contexts:
    web:
      place: web::connected::task
references:
- kind: code
  role: implementation
  target: src/store/tasks.ts
---

# Reopen task

## Trigger

The User reopens a completed one-off task.

## Outcome

The task is open again in its lists.
