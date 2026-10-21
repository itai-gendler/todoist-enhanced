---
availability:
- place: web::connected
- place: web::public
references:
- kind: code
  role: implementation
  target: src/domain/conflicts.ts
- kind: code
  role: implementation
  target: src/components/overlays/Issues.tsx
---

# Browse things to settle

Read enabled contradictions in task data and missing estimates separately. The app changes no conflicting task until the person chooses an action.
