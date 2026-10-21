---
availability:
- place: web::connected
- place: web::public
references:
- kind: code
  role: implementation
  target: src/components/BulkBar.tsx
- kind: code
  role: implementation
  target: src/components/overlays/TaskDetail.tsx
---

# Remove task tag

Remove a selected tag from the task or selection while preserving unrelated tags.
