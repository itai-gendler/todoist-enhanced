---
kind: validation
routes:
  web: Demo
steps:
- text: Choose a parent for selected tasks
  kind: actor
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Parent
  actor: visitor
  contexts:
    web:
      place: web::public::task
- text: The task nesting choice is invalid
  kind: condition
  entities:
  - entity: task
    effect: reads
    facts:
    - Parent
  contexts:
    web:
      place: web::public::task
- text: Keep the existing task placement
  kind: product
  entities:
  - entity: task
    effect: reads
    facts:
    - Parent
    - Project
    - Section
  actor: visitor
  contexts:
    web:
      place: web::public::task
references:
- kind: code
  role: implementation
  target: src/store/tasks-move.ts
- kind: code
  role: implementation
  target: src/domain/dnd.ts
---

# Reject an invalid nesting choice in the demo

## Trigger

The selection would contain its destination, create a cycle, or exceed four subtask levels. The visitor is using the disposable demo.

## Outcome

The nesting change is not submitted; the app leaves the work in its original places.
