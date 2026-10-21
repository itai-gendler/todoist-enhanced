---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor changes the project’s fields and saves
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

# Edit project in the demo

## Trigger

The Visitor chooses Edit on a project. The visitor is using the disposable demo.

## Outcome

The project shows its new name, icon, colour and description, and opens in the chosen list or board view. Changes affect demonstration work only; no request is sent to Todoist.
