---
kind: primary
routes:
  web: Connected account
steps:
- text: The User chooses Leave on the project
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
- text: The Product requests leaving and removes the project’s work from this account
  kind: product
  entities:
  - entity: project
    effect: changes
    facts:
    - Shared with me
  - entity: account
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
  target: src/domain/sharing.ts
- kind: code
  role: implementation
  target: src/store/collab.ts
- kind: code
  role: implementation
  target: src/components/overlays/ShareSheet.tsx
---

# Leave project

## Trigger

The User chooses Leave on a project another person shared with them.

## Outcome

The project, its sections and its tasks disappear from the app at once and a message confirms it; if Todoist refuses, they come back with a message.
