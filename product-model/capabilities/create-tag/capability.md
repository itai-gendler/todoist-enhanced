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

# Create tag

Create a named tag, normalizing spaces to hyphens and avoiding case-insensitive duplicates.
