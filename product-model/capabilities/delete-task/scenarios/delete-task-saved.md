---
kind: primary
routes:
  web: Connected account
steps:
- text: The User confirms deleting the task or the selected tasks
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
- text: The Product deletes the tasks with their subtasks and offers Undo
  kind: product
  entities:
  - entity: task
    effect: removes
    from: Open
  actor: user
  contexts:
    web:
      place: web::connected::task
references:
- kind: code
  role: implementation
  target: src/store/tasks.ts
---

# Delete task

## Trigger

The User chooses Delete on a task, or on several selected tasks, and confirms.

## Outcome

The tasks and their subtasks leave every list; Undo in the message brings them back.
