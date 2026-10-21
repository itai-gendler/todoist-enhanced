---
kind: primary
routes:
  web: Connected account
steps:
- text: The User chooses a parent task for the selection
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

# Make task a subtask

## Trigger

The User pulls a task a little to the right over another, or chooses a parent for the selected tasks.

## Outcome

The tasks become subtasks of the chosen task and take its project and section; a selected subtask stays under its selected parent.
