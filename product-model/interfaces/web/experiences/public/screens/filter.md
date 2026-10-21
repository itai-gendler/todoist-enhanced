---
entities:
- entity: filter
  shows:
  - Name
  - Query
  - Description
  - Colour
  - Favourite
  - Order
  - Frozen
- entity: task
  shows:
  - Title
  - Due date
  - Tags
  - Priority
  - Estimate
  - Completed on
references:
- kind: code
  role: implementation
  target: src/views/FiltersView.tsx
entryPoints:
- web: '#/filter/{filter}'
---

# Filter

Read a selected saved query and its matching work.
