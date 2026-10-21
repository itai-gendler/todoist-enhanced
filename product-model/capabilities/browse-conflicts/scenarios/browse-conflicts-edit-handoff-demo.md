---
kind: alternate
routes:
  web: Demo
steps:
- text: Choose Edit estimate for the task
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
      place: web::public::issues
- text: Open the affected task
  kind: product
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
references:
- kind: code
  role: implementation
  target: src/domain/conflicts.ts
- kind: code
  role: implementation
  target: src/components/overlays/Issues.tsx
---

# Open a task needing an estimate correction in the demo

## Trigger

An invalid estimate offers Edit estimate. The visitor is using the disposable demo.

## Outcome

The app opens the affected task for correction and closes Things to settle.
