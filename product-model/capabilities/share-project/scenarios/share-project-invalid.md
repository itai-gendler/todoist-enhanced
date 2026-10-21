---
kind: validation
routes:
  web: Connected account
steps:
- text: Enter an invitation email
  kind: actor
  entities: []
  actor: user
  contexts:
    web:
      place: web::connected::project
- text: The address is not valid input
  kind: condition
  entities: []
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

# Reject an invalid invitation address

## Trigger

The invitation address does not have an email-like form.

## Outcome

The address is marked invalid and no invitation request is made.
