---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor drags the project to a new place among its siblings
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

# Reorder projects in the demo

## Trigger

The Visitor drags a project to a new place in the sidebar. The visitor is using the disposable demo.

## Outcome

The project keeps its new place among the projects with the same parent and workspace. Changes affect demonstration work only; no request is sent to Todoist.
