---
kind: primary
routes:
  web: Demo
steps:
- text: Review task estimates in the conversion preview
  kind: actor
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Estimate
    - Native duration
  actor: visitor
  contexts:
    web:
      place: web::public::conversion
- text: Confirm conversion
  kind: actor
  entities: []
  actor: visitor
  contexts:
    web:
      place: web::public::conversion
- text: Convert the eligible task estimates
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Estimate
    - Tags
    - Native duration
  actor: visitor
  contexts:
    web:
      place: web::public::conversion
references:
- kind: code
  role: implementation
  target: src/components/overlays/EstimateConversion.tsx
- kind: code
  role: implementation
  target: src/domain/estimate-conversion.ts
- kind: code
  role: implementation
  target: src/store/estimate-safety.ts
---

# Convert durations to estimate tags in the demo

## Trigger

The person selects conversion to tags and reviews the preview. The visitor is using the disposable demo.

## Outcome

Eligible minute durations become estimate tags. Timed native calendar blocks remain; untimed native durations are cleared. Completed tasks and ambiguous estimates are skipped. Changes affect demonstration work only; no request is sent to Todoist.

## Edge cases

- Multiple or invalid estimate tags, disagreeing sources and day-unit durations are skipped.
- The preview identifies timed tasks affected and the skipped work.
