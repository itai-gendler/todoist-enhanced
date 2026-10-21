---
entities:
- entity: task
  shows:
  - Title
  - Due date
  - Tags
  - Estimate
  - Priority
  - Project
  - Section
  - Parent
  - Assignee
- entity: settings
  shows:
  - Daily capacity
  - Weekly override
references:
- kind: code
  role: implementation
  target: src/views/WeekView.tsx
entryPoints:
- web: '#/week'
---

# My week

Read overdue, today and flexible weekly commitments against weekly capacity. This context uses disposable demonstration work.
