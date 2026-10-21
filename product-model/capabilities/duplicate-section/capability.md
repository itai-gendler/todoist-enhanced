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
  target: src/components/SectionMenu.tsx
domain: projects
---

# Duplicate section

Create a new section below the original with copies of its open tasks and their subtask relationships.
