---
kind: edge
routes:
  web: Connected account
steps:
- text: Choose project access
  kind: actor
  entities:
  - entity: project
    effect: reads
    facts:
    - Name
    - Access
  actor: user
  contexts:
    web:
      place: web::connected::project
- text: Request the project visibility
  kind: product
  entities:
  - entity: project
    effect: changes
    facts:
    - Access
  actor: user
  contexts:
    web:
      place: web::connected::project
- text: The external request is refused
  kind: condition
  entities: []
  contexts:
    web:
      place: web::connected::project
- text: Restore the project access value
  kind: product
  entities:
  - entity: project
    effect: changes
    facts:
    - Access
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

# Restore access after an external refusal

## Trigger

Todoist rejects the requested visibility.

## Outcome

The app restores the prior project value and reports the refusal. Offering Public does not guarantee that Todoist enables it for the account.
