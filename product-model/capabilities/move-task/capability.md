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

# Move task

Move work into a selected project or section. A destination section determines its project; a move to a project root clears the section.
