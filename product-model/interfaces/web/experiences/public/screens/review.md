---
entities:
- entity: task
  shows:
  - Title
  - Due date
  - Estimate
  - Tags
  - Priority
  - Project
  - Assignee
  - Completed on
- entity: project
  shows:
  - Name
- entity: settings
  shows:
  - Daily capacity
  - Weekly override
  - Quiet delay
references:
- kind: code
  role: implementation
  target: src/views/ReviewView.tsx
entryPoints:
- web: '#/review'
---

# Review

Complete a daily or weekly review of existing work; progress belongs to the current pass. This context uses disposable demonstration work.
