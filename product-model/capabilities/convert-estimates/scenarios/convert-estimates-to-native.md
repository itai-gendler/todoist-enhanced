---
kind: alternate
routes:
  web: Connected account
steps:
- text: Review and confirm native conversion
  kind: actor
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Estimate
    - Tags
  actor: user
  contexts:
    web:
      place: web::connected::conversion
- text: Request and verify converted task estimates
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

# Convert tags to native durations

## Trigger

The person selects native conversion with an eligible account and confirms its preview.

## Outcome

Eligible estimate tags are replaced by requested native minute durations. Each item is reported as done, queued or failed; a downgrade to tags stops remaining native batches.
