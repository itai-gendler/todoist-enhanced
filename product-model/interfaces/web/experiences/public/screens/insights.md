---
entities:
- entity: task
  shows:
  - Title
  - Completed on
  - Project
  - Priority
  - Tags
  - Estimate
- entity: settings
  shows:
  - Dashboard arrangement
references:
- kind: code
  role: implementation
  target: src/views/InsightsView.tsx
entryPoints:
- web: '#/insights'
---

# Insights

Read the dashboard and Logbook for one selected period. This context uses disposable demonstration work.
