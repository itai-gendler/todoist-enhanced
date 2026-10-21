---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor chooses Skip to next occurrence
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
- text: The Product moves the demonstration task to its next occurrence
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Due date
    - Completed on
  actor: visitor
  contexts:
    web:
      place: web::public::task
references:
- kind: code
  role: implementation
  target: src/store/tasks.ts
---

# Skip to next occurrence in the demo

## Trigger

The Visitor chooses Skip to next occurrence on a repeating task, or on a selection. The visitor is using the disposable demo.

## Outcome

The demonstration task moves to its next occurrence, calculated locally; non-repeating tasks in the selection are left alone. Changes affect demonstration work only; no request is sent to Todoist.
