---
availability:
- place: web::connected
references:
- kind: code
  role: implementation
  target: src/store/sync.ts
- kind: code
  role: implementation
  target: src/api/auth.ts
---

# Disconnect account

Forget the connection on this device and clear its cached workspace and queued changes. The external OAuth grant remains managed in Todoist.
