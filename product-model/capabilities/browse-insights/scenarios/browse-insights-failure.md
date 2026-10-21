---
kind: edge
routes:
  web: Connected account
steps:
- text: Choose a history period
  kind: actor
  entities: []
  actor: user
  contexts:
    web:
      place: web::connected::insights
- text: The requested completion history is unavailable
  kind: condition
  entities: []
  contexts:
    web:
      place: web::connected::insights
- text: Retry the history request
  kind: actor
  entities: []
  actor: user
  contexts:
    web:
      place: web::connected::insights
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
---

# Retry a failed history read

## Trigger

The external completion-history request fails.

## Outcome

The page reports the failure and offers retry; values for a previous period are not relabelled as the requested period.
