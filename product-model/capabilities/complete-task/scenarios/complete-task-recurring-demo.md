---
kind: alternate
routes:
  web: Demo
steps:
- text: Complete the recurring task
  kind: actor
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Repeat rule
  actor: visitor
  contexts:
    web:
      place: web::public::task
- text: Advance the demonstration task’s next occurrence locally
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Due date
    - Completed on
    from: Open
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

# Complete a recurring occurrence in the demo

## Trigger

The person completes a recurring task. The visitor is using the disposable demo.

## Outcome

The demonstration advances the repeating task locally using its supported recurrence approximation. Changes affect demonstration work only; no request is sent to Todoist.
