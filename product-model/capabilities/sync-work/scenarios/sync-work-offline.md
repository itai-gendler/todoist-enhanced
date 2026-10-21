---
kind: edge
routes:
  web: Connected account
steps:
- text: Check the account connection after a local change
  kind: actor
  entities:
  - entity: account
    effect: reads
    facts:
    - Sync status
    - Pending changes
  actor: user
  contexts:
    web:
      place: web::connected::account
- text: Todoist cannot be reached
  kind: condition
  entities: []
  contexts:
    web:
      place: web::connected::account
- text: Retain pending changes and mark the account offline
  kind: product
  entities:
  - entity: account
    effect: changes
    facts:
    - Sync status
    - Pending changes
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
  target: src/api/client.ts
- kind: code
  role: implementation
  target: src/db/idb.ts
---

# Retain writes while offline

## Trigger

A workspace write is made while offline or the connection is lost.

## Outcome

Queued writes remain on this device for a later refresh; the account shows offline status and pending changes.
