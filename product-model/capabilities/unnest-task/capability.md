---
availability:
- place: web::connected
- place: web::public
references:
- kind: code
  role: implementation
  target: src/components/dnd/DragProvider.tsx
- kind: code
  role: implementation
  target: src/domain/dnd.ts
---

# Make task top-level

Lift a subtask out of its parent into its project or chosen section.
