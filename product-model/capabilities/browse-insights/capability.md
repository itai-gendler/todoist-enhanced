---
availability:
- place: web::connected
- place: web::public
references:
- kind: code
  role: implementation
  target: src/views/InsightsView.tsx
- kind: code
  role: implementation
  target: src/hooks/useCompleted.ts
- kind: code
  role: implementation
  target: src/api/completed.ts
- kind: code
  role: implementation
  target: src/domain/insights.ts
- kind: code
  role: implementation
  target: src/domain/logbook.ts
domain: insights
---

# Browse Insights

Read the dashboard and Logbook for a chosen day, week, month, quarter, year or custom period.
