---
kind: primary
routes:
  web: Connected account
steps:
- text: The User chooses another space for the project
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
- text: The Product moves the project to that workspace or to personal space and clears its former parent
  kind: product
  entities:
  - entity: project
    effect: changes
    facts:
    - Workspace
    - Parent
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

# Move project

## Trigger

The User moves a project to another space.

## Outcome

The project sits at the top level of its new space: a team workspace or personal space.
