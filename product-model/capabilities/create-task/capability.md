---
availability:
- place: web::connected
- place: web::public
references:
- kind: code
  role: implementation
  target: src/components/overlays/Composer.tsx
- kind: code
  role: implementation
  target: src/domain/shorthand.ts
- kind: code
  role: implementation
  target: src/store/tasks.ts
- kind: code
  role: implementation
  target: src/domain/dnd.ts
---

# Create task

Capture a task with optional scheduling, priority, tags, estimate, description, assignment and inline subtasks. Context supplies initial placement; a task without a chosen project goes to the Inbox.
