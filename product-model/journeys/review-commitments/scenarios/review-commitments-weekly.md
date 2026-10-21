---
kind: primary
result: achieved
routes:
  web: Connected account
steps:
- text: Start the review
  kind: actor
  actor: user
  capability: run-review
  entities: []
  contexts:
    web:
      place: web::connected::review
- text: Present the work that needs planning
  kind: product
  actor: user
  capability: run-review
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Due date
    - Estimate
  contexts:
    web:
      place: web::connected::review
- text: Choose a task commitment during the review
  kind: actor
  actor: user
  capability: schedule-task
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
  contexts:
    web:
      place: web::connected::review
- text: Save the task date and week commitment
  kind: product
  actor: user
  capability: schedule-task
  entities:
  - entity: task
    effect: changes
    facts:
    - Due date
    - Repeat rule
    - Tags
  contexts:
    web:
      place: web::connected::review
- text: Enter missing task estimates
  kind: actor
  actor: user
  capability: edit-task
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Estimate
  contexts:
    web:
      place: web::connected::review
- text: Save the task estimates
  kind: product
  actor: user
  capability: edit-task
  entities:
  - entity: task
    effect: changes
    facts:
    - Estimate
    - Tags
  contexts:
    web:
      place: web::connected::review
- text: Finish the review after its capacity question
  kind: actor
  actor: user
  capability: run-review
  entities: []
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

# Review commitments

## Trigger

The person starts a weekly review.

## Outcome

The pass ends after the person has read its prompts and saved the planning changes they chose.
