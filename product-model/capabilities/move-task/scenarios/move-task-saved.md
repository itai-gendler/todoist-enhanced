---
kind: primary
routes:
  web: Connected account
steps:
- text: The User chooses a destination for the tasks
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

# Move task

## Trigger

The User moves a task, or several selected tasks, to a project or a section.

## Outcome

The tasks belong to the chosen section and its project, or to the project root with no section.
