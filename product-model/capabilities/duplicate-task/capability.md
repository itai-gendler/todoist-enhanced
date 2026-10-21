---
availability:
- place: web::connected
- place: web::public
references:
- kind: code
  role: implementation
  target: src/store/tasks.ts
---

# Duplicate task

Create an open copy of a task and its open subtask branch; task comments are left with the original.
