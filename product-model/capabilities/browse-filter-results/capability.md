---
availability:
- place: web::connected
- place: web::public
references:
- kind: code
  role: implementation
  target: src/hooks/useFilterResult.ts
- kind: code
  role: implementation
  target: src/api/filters.ts
- kind: code
  role: implementation
  target: src/views/SimpleListView.tsx
domain: filters
---

# Browse filter results

Read the tasks Todoist returns for a saved query. The demo supports its supplied example queries without an external query engine.
