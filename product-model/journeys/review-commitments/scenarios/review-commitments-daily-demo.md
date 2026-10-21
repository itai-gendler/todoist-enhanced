---
kind: primary
result: achieved
routes:
  web: Demo
steps:
- text: Start the review
  kind: actor
  actor: visitor
  capability: run-review
  entities: []
  contexts:
    web:
      place: web::public::review
- text: Present the work that needs planning
  kind: product
  actor: visitor
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
      place: web::public::review
- text: Choose a task commitment during the review
  kind: actor
  actor: visitor
  capability: schedule-task
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
  contexts:
    web:
      place: web::public::review
- text: Save the task date and week commitment
  kind: product
  actor: visitor
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
      place: web::public::review
- text: Enter missing task estimates
  kind: actor
  actor: visitor
  capability: edit-task
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Estimate
  contexts:
    web:
      place: web::public::review
- text: Save the task estimates
  kind: product
  actor: visitor
  capability: edit-task
  entities:
  - entity: task
    effect: changes
    facts:
    - Estimate
    - Tags
  contexts:
    web:
      place: web::public::review
- text: Finish the review after its capacity question
  kind: actor
  actor: visitor
  capability: run-review
  entities: []
  contexts:
    web:
      place: web::public::review
references:
- kind: code
  role: implementation
  target: src/views/ReviewView.tsx
- kind: code
  role: implementation
  target: src/domain/review.ts
---

# Review commitments in the demo

## Trigger

The person starts a daily review.

## Outcome

The pass ends after the person has read its prompts and saved the planning changes they chose.
