---
kind: primary
routes:
  web: Connected account
steps:
- text: The User chooses an access level for the project
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
- text: The Product requests the chosen access level for the project
  kind: product
  entities:
  - entity: project
    effect: changes
    facts:
    - Access
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
  target: src/domain/projectAccess.ts
- kind: code
  role: implementation
  target: src/components/overlays/ShareSheet.tsx
---

# Change project access

## Trigger

The User chooses another access level in a project’s sharing view.

## Outcome

The project shows the requested access: Restricted or Public for a personal project, and Team as well in a workspace. A value Todoist returns that the app does not know stays shown as it is.
