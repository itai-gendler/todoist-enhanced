---
kind: primary
routes:
  web: Connected account
steps:
- text: The User enters an email address and chooses Invite in the project’s sharing view
  kind: actor
  entities:
  - entity: project-member
    effect: reads
    facts:
    - Name
  - entity: project
    effect: reads
    facts:
    - Name
  actor: user
  contexts: &id001
    web:
      place: web::connected::project
- kind: condition
  text: Todoist accepts the invitation request and returns the new participation
  entities: []
  contexts: *id001
- text: The Product sends the invitation and refreshes the project’s people
  kind: product
  entities:
  - entity: project-member
    effect: creates
    facts:
    - Name
    - Email
    - Role
    - Participation
  - entity: project
    effect: reads
    facts:
    - Name
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
  target: src/components/overlays/ShareSheet.tsx
- kind: code
  role: implementation
  target: src/store/collab.ts
---

# Share project

## Trigger

The User invites someone by email in a project’s sharing view.

## Outcome

The invitation request is sent and the project’s people are refreshed. A workspace invitation can ask for Collaborator or Admin; a personal one has no role choice. Delivering and accepting the invitation belong to Todoist.
