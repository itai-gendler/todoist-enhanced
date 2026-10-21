---
kind: primary
routes:
  web: Connected account
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
  actor: user
  contexts:
    web:
      place: web::connected::conversion
- text: Confirm conversion
  kind: actor
  entities: []
  actor: user
  contexts:
    web:
      place: web::connected::conversion
- text: Convert the eligible task estimates
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Estimate
    - Tags
    - Native duration
  actor: user
  contexts:
    web:
      place: web::connected::conversion
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

# Convert durations to estimate tags

## Trigger

The person selects conversion to tags and reviews the preview.

## Outcome

Eligible minute durations become estimate tags. Timed native calendar blocks remain; untimed native durations are cleared. Completed tasks and ambiguous estimates are skipped.

## Edge cases

- Multiple or invalid estimate tags, disagreeing sources and day-unit durations are skipped.
- The preview identifies timed tasks affected and the skipped work.
