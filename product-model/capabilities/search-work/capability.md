---
availability:
- place: web::connected
- place: web::public
references:
- kind: code
  role: implementation
  target: src/components/overlays/Search.tsx
- kind: code
  role: implementation
  target: src/views/SearchView.tsx
- kind: code
  role: implementation
  target: src/domain/search.ts
---

# Search work

Search task titles and descriptions, projects, tags, optional sections, and built-in destinations using case- and accent-insensitive matching.
