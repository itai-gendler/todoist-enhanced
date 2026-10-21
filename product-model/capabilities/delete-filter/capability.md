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
  target: src/components/overlays/FilterSheet.tsx
domain: filters
---

# Delete filter

Delete a saved filter after confirmation; the tasks matched by it remain.
