---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor takes the subtask out of its parent
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
  actor: visitor
  contexts:
    web:
      place: web::public::task
references:
- kind: code
  role: implementation
  target: src/components/dnd/DragProvider.tsx
- kind: code
  role: implementation
  target: src/domain/dnd.ts
---

# Make task top-level in the demo

## Trigger

The Visitor pulls a subtask out to the left, or makes it a task of its own. The visitor is using the disposable demo.

## Outcome

The task is top-level again, in its project or in the chosen section. Changes affect demonstration work only; no request is sent to Todoist.
