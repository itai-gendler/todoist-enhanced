---
kind: alternate
routes:
  web: Connected account
steps:
- text: Choose Edit estimate for the task
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
      place: web::connected::issues
- text: Open the affected task
  kind: product
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Estimate
  actor: user
  contexts:
    web:
      place: web::connected::task
references:
- kind: code
  role: implementation
  target: src/domain/conflicts.ts
- kind: code
  role: implementation
  target: src/components/overlays/Issues.tsx
---

# Open a task needing an estimate correction

## Trigger

An invalid estimate offers Edit estimate.

## Outcome

The app opens the affected task for correction and closes Things to settle.
