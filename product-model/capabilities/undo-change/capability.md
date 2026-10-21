---
availability:
- place: web::connected
- place: web::public
references:
- kind: code
  role: implementation
  target: src/store/ui.ts
- kind: code
  role: implementation
  target: src/store/tasks.ts
- kind: code
  role: implementation
  target: src/store/tasks-move.ts
---

# Undo change

Reverse the latest recorded reversible change during this session. Undo is limited to operations that record it; it is not persistent document history.
