---
kind: primary
routes:
  web: Connected account
steps:
- text: The User takes the subtask out of its parent
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
- text: The Product makes the task top-level in its project or the chosen section
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Parent
    - Project
    - Section
    - Order
  - entity: project
    effect: reads
    facts:
    - Name
  - entity: section
    effect: reads
    facts:
    - Name
  actor: user
  contexts:
    web:
      place: web::connected::task
references:
- kind: code
  role: implementation
  target: src/components/dnd/DragProvider.tsx
- kind: code
  role: implementation
  target: src/domain/dnd.ts
---

# Make task top-level

## Trigger

The User pulls a subtask out to the left, or makes it a task of its own.

## Outcome

The task is top-level again, in its project or in the chosen section.
