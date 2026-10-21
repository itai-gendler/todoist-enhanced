---
kind: edge
routes:
  web: Connected account
steps:
- text: Refresh the account after pending writes
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
- text: Reconcile the task changes and report account status
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Title
    - Description
    - Due date
    - Tags
    - Priority
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

# Report refused writes

## Trigger

Todoist returns a refusal for one or more submitted operations.

## Outcome

The app reverses the refused optimistic changes, reports the refusal and preserves accepted changes. Invalid account credentials return the user to Connect.
