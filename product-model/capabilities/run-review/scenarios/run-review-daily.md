---
kind: primary
routes:
  web: Connected account
steps:
- text: Start the daily review
  kind: actor
  entities: []
  actor: user
  contexts:
    web:
      place: web::connected::review
- text: Present the tasks and daily capacity in review order
  kind: product
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Due date
    - Tags
    - Estimate
    - Project
  - entity: settings
    effect: reads
    facts:
    - Daily capacity
  actor: user
  contexts:
    web:
      place: web::connected::review
- text: Advance through the questions and finish
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

# Complete a daily review

## Trigger

The person chooses the daily cadence.

## Outcome

The review reaches its end after overdue work, external mail, Inbox filing, undated weekly commitments, missing estimates and today’s capacity. Each action changes the underlying work immediately.

## Edge cases

- The mail step only opens external mail clients; it neither reads nor verifies mail.
- Empty steps are still shown. Next and Finish do not require every task to be resolved.
- Leaving the review discards pass progress and unsaved estimate drafts, not already saved work.
