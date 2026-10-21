---
entities:
- entity: task
  shows:
  - Title
  - Due date
  - Repeat rule
  - Estimate
  - Priority
  - Project
references:
- kind: code
  role: implementation
  target: src/views/UpcomingView.tsx
entryPoints:
- web: '#/upcoming'
---

# Upcoming

Read future-dated work and supported recurring forecasts.
