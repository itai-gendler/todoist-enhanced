---
kind: primary
routes:
  web: Connected account
steps:
- text: The User drags the project to a new place among its siblings
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
- text: The Product saves the order of the projects within that parent and workspace
  kind: product
  entities:
  - entity: project
    effect: changes
    facts:
    - Order
  - entity: workspace
    effect: reads
    facts:
    - Name
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

# Reorder projects

## Trigger

The User drags a project to a new place in the sidebar.

## Outcome

The project keeps its new place among the projects with the same parent and workspace.
