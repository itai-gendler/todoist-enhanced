---
kind: alternate
routes:
  web: Connected account
steps:
- text: Complete the recurring task
  kind: actor
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Repeat rule
  actor: user
  contexts:
    web:
      place: web::connected::task
- text: Read the task’s next occurrence from Todoist
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Due date
    - Completed on
    from: Open
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

# Complete a recurring occurrence

## Trigger

The person completes a recurring task.

## Outcome

The app requests recurrence-aware completion and adopts the next open occurrence returned by Todoist; it can temporarily show completion while awaiting that result.
