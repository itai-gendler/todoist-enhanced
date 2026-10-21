---
kind: primary
routes:
  web: Connected account
steps:
- text: The User chooses Skip to next occurrence
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
- text: The Product completes the current occurrence and reads the next one from Todoist
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Due date
    - Completed on
  actor: user
  contexts:
    web:
      place: web::connected::task
references:
- kind: code
  role: implementation
  target: src/store/tasks.ts
---

# Skip to next occurrence

## Trigger

The User chooses Skip to next occurrence on a repeating task, or on a selection.

## Outcome

The returned next occurrence is shown. The skip uses Todoist’s completion of a repeating task, and non-repeating tasks in the selection are left alone.
