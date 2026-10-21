---
kind: primary
routes:
  web: Connected account
steps:
- text: The User picks Collaborator or Admin for a member
  kind: actor
  entities:
  - entity: project-member
    effect: reads
    facts:
    - Name
  actor: user
  contexts:
    web:
      place: web::connected::project
- text: The Product requests the new role and refreshes the project’s members
  kind: product
  entities:
  - entity: project-member
    effect: changes
    facts:
    - Role
  - entity: project
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
  target: src/components/overlays/ShareSheet.tsx
- kind: code
  role: implementation
  target: src/store/collab.ts
---

# Change project member role

## Trigger

The User changes the role of a member in a team project’s sharing view.

## Outcome

The member holds the new role once Todoist accepts it, and the member list is refreshed. Older role names Todoist returns stay readable.
