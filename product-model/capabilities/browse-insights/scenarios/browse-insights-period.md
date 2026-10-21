---
kind: primary
routes:
  web: Connected account
steps:
- text: Choose the reporting period
  kind: actor
  entities: []
  actor: user
  contexts:
    web:
      place: web::connected::insights
- text: Read completed tasks and derive the reporting figures
  kind: product
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Completed on
    - Project
    - Priority
    - Tags
    - Estimate
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

# Read a period and its Logbook

## Trigger

The person chooses an Insights period.

## Outcome

Dashboard and Logbook share the period. The dashboard derives completion totals, estimated time, priority focus, project/tag distributions and streaks; the Logbook can filter several projects and priorities and group completed work.

## Edge cases

- Estimated completed minutes are not measured time spent; tasks with no estimate are counted separately.
- Comparisons use the immediately preceding interval of the same number of calendar days.
- A quarter is summarized by month, and weeks use the account’s start day.
