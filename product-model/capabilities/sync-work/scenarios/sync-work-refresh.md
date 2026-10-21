---
kind: primary
routes:
  web: Connected account
steps:
- text: Request a fresh account copy
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
- text: Send pending account changes and read the response
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

# Refresh queued work

## Trigger

The user requests a refresh.

## Outcome

Queued writes are sent before the fresh workspace is read. The account reports the resulting status and pending count.
