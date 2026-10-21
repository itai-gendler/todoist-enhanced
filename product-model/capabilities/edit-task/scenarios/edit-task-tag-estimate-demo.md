---
kind: alternate
routes:
  web: Demo
steps:
- text: Enter the task estimate
  kind: actor
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Estimate
  actor: visitor
  contexts:
    web:
      place: web::public::task
- text: Save the task estimate and its tags
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Estimate
    - Tags
  - entity: tag
    effect: reads
    facts:
    - Name
  actor: visitor
  contexts:
    web:
      place: web::public::task
references:
- kind: code
  role: implementation
  target: src/components/overlays/TaskDetail.tsx
- kind: code
  role: implementation
  target: src/components/Checklist.tsx
- kind: code
  role: implementation
  target: src/store/tasks.ts
- kind: code
  role: implementation
  target: src/domain/estimates.ts
- kind: code
  role: implementation
  target: src/store/estimate-safety.ts
- kind: code
  role: implementation
  target: src/components/overlays/Unestimated.tsx
---

# Save an estimate in tags in the demo

## Trigger

Tags is the selected estimate storage. The visitor is using the disposable demo.

## Outcome

A valid input such as 1h15 becomes 75 estimated minutes. Existing estimate tags are replaced with one est-75 tag; unrelated tags and native calendar duration remain. Changes affect demonstration work only; no request is sent to Todoist.

## Edge cases

- Clearing a tag estimate removes estimate tags without clearing native duration.
- An invalid or nonpositive duration is not a saved estimate.
