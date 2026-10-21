---
kind: primary
routes:
  web: Connected account
steps:
- text: The User chooses Duplicate on the project
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
- text: The Product creates a copy of the project with its active sections and open tasks
  kind: product
  entities:
  - entity: project
    effect: creates
    facts:
    - Name
    - Colour
    - Description
    - Workspace
    to: Active
  - entity: section
    effect: creates
    facts:
    - Name
    - Project
    to: Active
    with: project
  - entity: task
    effect: creates
    facts:
    - Title
    - Description
    - Project
    - Section
    - Priority
    - Tags
    - Due date
    to: Open
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

# Duplicate project

## Trigger

The User chooses Duplicate on a project.

## Outcome

A new project appears with the original’s description and colour, its active sections and copies of its open tasks.
