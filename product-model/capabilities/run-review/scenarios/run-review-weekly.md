---
kind: alternate
routes:
  web: Connected account
steps:
- text: Choose the weekly review and history week
  kind: actor
  entities: []
  actor: user
  contexts:
    web:
      place: web::connected::review
- text: Present completion history and current planning tasks
  kind: product
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Completed on
    - Due date
    - Tags
    - Estimate
  - entity: project
    effect: reads
    facts:
    - Name
  - entity: settings
    effect: reads
    facts:
    - Weekly override
    - Daily capacity
  actor: user
  contexts:
    web:
      place: web::connected::review
- text: Read the prompts and finish
  kind: actor
  entities: []
  actor: user
  contexts:
    web:
      place: web::connected::review
references:
- kind: code
  role: implementation
  target: src/views/ReviewView.tsx
- kind: code
  role: implementation
  target: src/domain/review.ts
---

# Close a week and consider the next

## Trigger

The person chooses the weekly cadence.

## Outcome

The pass reports completions and statistics, then overdue work and quiet-project candidates, followed by mail, Inbox, Someday, weekly commitments, estimates and weekly load.

## Edge cases

- The first two days of the account’s week default to reviewing the previous week; later days default to the current week.
- Choosing another cadence restarts the pass. Historical week selection changes completion reports; current planning work remains current.
