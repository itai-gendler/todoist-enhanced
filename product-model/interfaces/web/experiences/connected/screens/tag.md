---
entities:
- entity: tag
  shows:
  - Name
  - Colour
  - Favourite
  - Order
  - Reserved
- entity: task
  shows:
  - Title
  - Tags
  - Due date
  - Estimate
  - Priority
references:
- kind: code
  role: implementation
  target: src/views/LabelsView.tsx
entryPoints:
- web: '#/label/{tag}'
---

# Tag

Read work carrying a selected tag.
