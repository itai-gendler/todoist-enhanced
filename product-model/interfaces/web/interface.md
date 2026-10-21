---
type: web
actors:
- visitor
- user
entryPoints:
- web: /
references:
- kind: code
  role: implementation
  target: src/App.tsx
- kind: code
  role: implementation
  target: src/hooks/useRoute.ts
---

# Web app

The browser application, including its installable and responsive use. Todoist is an outbound dependency; the internal adapters are not public APIs of this product.
