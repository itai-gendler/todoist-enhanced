---
availability:
- place: web::connected
references:
- kind: code
  role: implementation
  target: src/components/overlays/ShareSheet.tsx
- kind: code
  role: implementation
  target: src/store/collab.ts
domain: projects
---

# Remove project member

Request removal of a current member or cancellation of a pending invitation, then refresh the returned people.
