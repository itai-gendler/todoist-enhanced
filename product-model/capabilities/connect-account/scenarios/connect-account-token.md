---
kind: alternate
routes:
  web: Connect
steps:
- text: Submit a personal token
  kind: actor
  entities: []
  actor: visitor
  contexts:
    web:
      place: web::public::connect
- text: Read the account using the supplied credential
  kind: product
  entities:
  - entity: account
    effect: creates
    facts:
    - Name
    - Email
    - Week start
    - Plan
    - Duration storage allowed
    - Connection method
    - Sync status
    - Pending changes
  actor: visitor
  contexts:
    web:
      place: web::public::connect
references:
- kind: code
  role: implementation
  target: src/views/ConnectView.tsx
- kind: code
  role: implementation
  target: src/api/oauth.ts
- kind: code
  role: implementation
  target: src/api/auth.ts
- kind: code
  role: implementation
  target: src/store/sync.ts
---

# Connect using a personal token

## Trigger

The visitor selects the token alternative.

## Outcome

A successful workspace read connects the account; the token stays on this device.
