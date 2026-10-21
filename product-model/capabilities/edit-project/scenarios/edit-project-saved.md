---
kind: primary
routes:
  web: Connected account
steps:
- text: The User changes the project’s fields and saves
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
- text: The Product saves the project’s name, description, icon, colour and initial view
  kind: product
  entities:
  - entity: project
    effect: changes
    facts:
    - Name
    - Description
    - Colour
    - Default view
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

# Edit project

## Trigger

The User chooses Edit on a project.

## Outcome

The project shows its new name, icon, colour and description, and opens in the chosen list or board view.
