---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor names a new project and chooses where it goes
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
- text: The Product creates the project in personal space or the chosen workspace
  kind: product
  entities:
  - entity: project
    effect: creates
    facts:
    - Inbox
    - Name
    - Description
    - Colour
    - Favourite
    - Workspace
    - Parent
    - Order
    - Access
    - My role
    - Access editing available
    - People management available
    - Assignment allowed
    - Shared with me
    - Default view
    to: Active
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

# Create project in the demo

## Trigger

The Visitor adds a project. The visitor is using the disposable demo.

## Outcome

The new project appears in personal space or the chosen workspace, with the chosen description, icon, colour, access and initial list or board view. Changes affect demonstration work only; no request is sent to Todoist.
