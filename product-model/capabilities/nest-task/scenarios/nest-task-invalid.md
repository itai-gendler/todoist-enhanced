---
kind: validation
routes:
  web: Connected account
steps:
- text: Choose a parent for selected tasks
  kind: actor
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Parent
  actor: user
  contexts:
    web:
      place: web::connected::task
- text: The task nesting choice is invalid
  kind: condition
  entities:
  - entity: task
    effect: reads
    facts:
    - Parent
  contexts:
    web:
      place: web::connected::task
- text: Keep the existing task placement
  kind: product
  entities:
  - entity: task
    effect: reads
    facts:
    - Parent
    - Project
    - Section
  actor: user
  contexts:
    web:
      place: web::connected::task
references:
- kind: code
  role: implementation
  target: src/store/tasks-move.ts
- kind: code
  role: implementation
  target: src/domain/dnd.ts
---

# Reject an invalid nesting choice

## Trigger

The selection would contain its destination, create a cycle, or exceed four subtask levels.

## Outcome

The nesting change is not submitted; the app leaves the work in its original places.
