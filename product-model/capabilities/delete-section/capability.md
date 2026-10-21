---
availability:
- place: web::connected
- place: web::public
references:
- kind: code
  role: implementation
  target: src/components/SectionMenu.tsx
- kind: code
  role: implementation
  target: src/store/structure.ts
domain: projects
---

# Delete section

Delete a section after moving its tasks to the project root. The tasks are retained.
