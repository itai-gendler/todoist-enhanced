---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor chooses a parent task for the selection
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
- text: The Product places the selected tasks under the parent, in its project and section
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
  target: src/store/tasks-move.ts
- kind: code
  role: implementation
  target: src/domain/dnd.ts
---

# Make task a subtask in the demo

## Trigger

The Visitor pulls a task a little to the right over another, or chooses a parent for the selected tasks. The visitor is using the disposable demo.

## Outcome

The tasks become subtasks of the chosen task and take its project and section; a selected subtask stays under its selected parent. Changes affect demonstration work only; no request is sent to Todoist.
