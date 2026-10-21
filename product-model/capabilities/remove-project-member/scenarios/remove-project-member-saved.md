---
kind: primary
routes:
  web: Connected account
steps:
- text: The User chooses Remove on the person or the pending invitation
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
- text: The Product requests the removal and refreshes the people listed
  kind: product
  entities:
  - entity: project-member
    effect: removes
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

# Remove project member

## Trigger

The User chooses Remove on a person, or on a pending invitation, in a project’s sharing view.

## Outcome

Once Todoist accepts the request, the person or the invitation is no longer listed.
