---
entities:
- entity: task
  shows:
  - Title
  - Due date
  - Priority
  - Tags
  - Estimate
- entity: settings
  shows:
  - Matrix rules
references:
- kind: code
  role: implementation
  target: src/views/EisenhowerView.tsx
entryPoints:
- web: '#/matrix'
---

# Eisenhower matrix

Read work by urgency and importance. This context uses disposable demonstration work.
