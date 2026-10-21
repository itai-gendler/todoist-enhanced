---
kind: alternate
routes:
  web: Connected account
steps:
- text: A visible online session reaches a refresh trigger
  kind: condition
  entities: []
  unattended: true
  contexts:
    web:
      place: web::connected::account
- text: Refresh the account copy and pending count
  kind: product
  entities:
  - entity: account
    effect: changes
    facts:
    - Sync status
    - Pending changes
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

# Refresh when the app returns online

## Trigger

The page is visible and online at the polling interval, or regains focus, visibility or connectivity.

## Outcome

The same refresh process updates the visible connection status.
