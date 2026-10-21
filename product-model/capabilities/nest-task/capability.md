---
availability:
- place: web::connected
- place: web::public
references:
- kind: code
  role: implementation
  target: src/store/tasks-move.ts
- kind: code
  role: implementation
  target: src/domain/dnd.ts
---

# Make task a subtask

Place selected task branches under another task, adopting its project and section and keeping selected descendants with their selected ancestor.
