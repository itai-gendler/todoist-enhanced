---
availability:
- place: web::connected
- place: web::public
references:
- kind: code
  role: implementation
  target: src/store/tasks.ts
---

# Delete task

Remove selected tasks and their subtasks after confirmation, with an undo opportunity.
