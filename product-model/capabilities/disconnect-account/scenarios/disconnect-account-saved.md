---
kind: primary
routes:
  web: Connected account
steps:
- text: The User chooses Disconnect
  kind: actor
  entities:
  - entity: account
    effect: reads
    facts:
    - Name
  actor: user
  contexts:
    web:
      place: web::connected::account
- text: The Product forgets the account on this device with its cached work and waiting changes
  kind: product
  entities:
  - entity: account
    effect: removes
  actor: user
  contexts:
    web:
      place: web::connected::account
references:
- kind: code
  role: implementation
  target: src/store/sync.ts
- kind: code
  role: implementation
  target: src/api/auth.ts
---

# Disconnect account

## Trigger

The User chooses Disconnect in Account.

## Outcome

The app returns to Connect, and this device no longer holds the connection, the cached work or the changes still waiting to be sent. The app’s access stays listed in Todoist’s integrations until it is removed there.
