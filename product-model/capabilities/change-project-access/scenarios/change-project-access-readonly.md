---
kind: validation
routes:
  web: Connected account
steps:
- kind: actor
  actor: user
  text: The User opens the project’s sharing view
  entities:
  - entity: project
    effect: reads
    facts:
    - Name
    - Access
    - Access editing available
  contexts: &id001
    web:
      place: web::connected::project
- kind: condition
  text: The sharing view receives a project role without access editing.
  entities:
  - entity: project
    effect: reads
    facts:
    - Name
    - Access
    - Access editing available
  contexts: *id001
- kind: product
  actor: user
  text: The existing visibility is shown as a read-only value in sharing.
  entities:
  - entity: project
    effect: reads
    facts:
    - Name
    - Access
    - Access editing available
  contexts: *id001
references:
- kind: code
  role: implementation
  target: src/domain/projectAccess.ts
- kind: code
  role: implementation
  target: src/components/overlays/ShareSheet.tsx
---

# Read existing project visibility

## Trigger

The sharing view receives a project role without access editing.

## Outcome

The existing visibility is shown as a read-only value in sharing.
