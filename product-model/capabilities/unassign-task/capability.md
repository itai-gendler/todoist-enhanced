---
availability:
- place: web::connected
references:
- kind: code
  role: implementation
  target: src/domain/assignees.ts
- kind: code
  role: implementation
  target: src/domain/sharing.ts
- kind: code
  role: implementation
  target: src/store/collab.ts
- kind: code
  role: implementation
  target: src/components/AssigneeField.tsx
---

# Unassign task

Remove the task’s assignee when assignment is available for that project.
