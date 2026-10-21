---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor confirms deleting the project
  kind: actor
  entities:
  - entity: project
    effect: reads
    facts:
    - Inbox
  actor: visitor
  contexts:
    web:
      place: web::public::project
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
  actor: visitor
  contexts:
    web:
      place: web::public::project
references:
- kind: code
  role: implementation
  target: src/store/structure.ts
- kind: code
  role: implementation
  target: src/components/ProjectMenu.tsx
---

# Delete project in the demo

## Trigger

The Visitor chooses Delete on a project and confirms. The visitor is using the disposable demo.

## Outcome

The project is deleted with its sections and tasks; the confirmation said how many tasks go with it. Changes affect demonstration work only; no request is sent to Todoist.
