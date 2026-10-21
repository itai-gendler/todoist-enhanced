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
  target: src/components/overlays/TagSheet.tsx
domain: tags
---

# Delete tag

Delete a tag and remove it from the tasks that carry it.
