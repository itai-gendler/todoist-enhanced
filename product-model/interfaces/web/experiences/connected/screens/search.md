---
entities:
- entity: task
  shows:
  - Title
  - Description
- entity: project
  shows:
  - Name
- entity: section
  shows:
  - Name
- entity: tag
  shows:
  - Name
references:
- kind: code
  role: implementation
  target: src/components/overlays/Search.tsx
entryPoints:
- web: '#/search?q={query}'
---

# Search

Find tasks, projects, sections, tags and destinations.
