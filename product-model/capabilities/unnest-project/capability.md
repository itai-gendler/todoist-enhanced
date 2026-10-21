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

# Move project to top level

Return a nested project to the top level of its workspace.
