---
availability:
- place: web::connected
- place: web::public
references:
- kind: code
  role: implementation
  target: src/views/FiltersView.tsx
- kind: code
  role: implementation
  target: src/hooks/useFilterResult.ts
domain: filters
---

# Browse filters

Read saved filter names, queries, favourites and available match counts.
