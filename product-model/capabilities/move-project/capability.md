---
availability:
- place: web::connected
- place: web::public
references:
- kind: code
  role: implementation
  target: src/store/structure.ts
- kind: code
  role: implementation
  target: src/components/ProjectMenu.tsx
domain: projects
---

# Move project

Move a project between an existing team workspace and personal space, clearing its former parent placement.
