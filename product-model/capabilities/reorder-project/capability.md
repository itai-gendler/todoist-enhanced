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

# Reorder projects

Drag a project to a new place among the projects with the same parent and workspace.
