---
kind: primary
routes:
  web: Connected account
steps:
- text: The User confirms deleting the project
  kind: actor
  entities:
  - entity: project
    effect: reads
    facts:
    - Inbox
  actor: user
  contexts:
    web:
      place: web::connected::project
- text: The Product deletes the project with its sections and tasks
  kind: product
  entities:
  - entity: project
    effect: removes
    from: Active
  - entity: section
    effect: removes
    from: Active
    with: project
  - entity: task
    effect: removes
    from: Open
    with: project
  actor: user
  contexts:
    web:
      place: web::connected::project
references:
- kind: code
  role: implementation
  target: src/store/structure.ts
- kind: code
  role: implementation
  target: src/components/ProjectMenu.tsx
---

# Delete project

## Trigger

The User chooses Delete on a project and confirms.

## Outcome

The project is deleted with its sections and tasks; the confirmation said how many tasks go with it.
