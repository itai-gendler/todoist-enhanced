---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor chooses a destination for the tasks
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
- text: The Product moves the tasks to the chosen section and its project, or to the project root
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Project
    - Section
    - Parent
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

# Move task in the demo

## Trigger

The Visitor moves a task, or several selected tasks, to a project or a section. The visitor is using the disposable demo.

## Outcome

The tasks belong to the chosen section and its project, or to the project root with no section. Changes affect demonstration work only; no request is sent to Todoist.
