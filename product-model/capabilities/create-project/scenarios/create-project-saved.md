---
kind: primary
routes:
  web: Connected account
steps:
- text: The User names a new project and chooses where it goes
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

# Create project

## Trigger

The User adds a project.

## Outcome

The new project appears in personal space or the chosen workspace, with the chosen description, icon, colour, access and initial list or board view.
