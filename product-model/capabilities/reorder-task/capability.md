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
- kind: code
  role: implementation
  target: src/store/tasks.ts
---

# Reorder task

Save the chosen task or subtask order. Reordering visible work preserves the relative slots of tasks hidden by filters.
