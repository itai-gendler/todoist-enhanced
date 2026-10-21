---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor confirms deleting the task or the selected tasks
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
- text: The Product deletes the tasks with their subtasks and offers Undo
  kind: product
  entities:
  - entity: task
    effect: removes
    from: Open
  actor: visitor
  contexts:
    web:
      place: web::public::task
references:
- kind: code
  role: implementation
  target: src/store/tasks.ts
---

# Delete task in the demo

## Trigger

The Visitor chooses Delete on a task, or on several selected tasks, and confirms. The visitor is using the disposable demo.

## Outcome

The tasks and their subtasks leave every list; Undo in the message brings them back. Changes affect demonstration work only; no request is sent to Todoist.
