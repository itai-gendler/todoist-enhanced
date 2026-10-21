---
availability:
- place: web::connected
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

# Sync work

Refresh the account copy, send queued writes, and show pending work or failures. Outbound Todoist responses determine which changes were accepted.
