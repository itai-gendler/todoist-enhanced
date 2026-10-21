---
entities:
- entity: task
  shows:
  - Title
  - Due date
  - Tags
  - Estimate
  - Priority
  - Assignee
- entity: settings
  shows:
  - Daily capacity
references:
- kind: code
  role: implementation
  target: src/views/WeekView.tsx
entryPoints:
- web: '#/today'
---

# Today

Read overdue and today’s work against today’s capacity. This context uses disposable demonstration work.
