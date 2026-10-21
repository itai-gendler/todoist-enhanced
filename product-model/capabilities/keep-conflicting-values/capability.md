---
availability:
- place: web::connected
- place: web::public
references:
- kind: code
  role: implementation
  target: src/components/overlays/Issues.tsx
- kind: code
  role: implementation
  target: src/domain/conflicts.ts
---

# Keep conflicting values

Leave a reported contradiction as it is, with Keep both or Keep the parent estimate, without changing the task.
