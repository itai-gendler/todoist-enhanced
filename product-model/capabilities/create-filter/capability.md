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

# Create filter

Create a saved filter with a nonempty name and query; Todoist evaluates the query when it is opened.
