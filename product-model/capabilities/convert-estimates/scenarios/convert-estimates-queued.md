---
kind: edge
routes:
  web: Connected account
steps:
- text: Confirm the conversion preview
  kind: actor
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Estimate
  actor: user
  contexts:
    web:
      place: web::connected::conversion
- text: Queue converted task estimates
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Estimate
    - Tags
  actor: user
  contexts:
    web:
      place: web::connected::conversion
- text: The network has not confirmed these changes
  kind: condition
  entities: []
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

# Keep conversion results pending offline

## Trigger

A confirmed conversion cannot finish sending or verifying its writes.

## Outcome

Its own pending items remain queued rather than being called successful because unrelated writes finished.
