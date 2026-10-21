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

# Edit tag

Rename a tag or change its colour; a renamed tag is renamed on the tasks that carry it.
