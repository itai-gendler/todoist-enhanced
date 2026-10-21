---
kind: primary
routes:
  web: Connected account
steps:
- text: Open Things to settle
  kind: actor
  entities: []
  actor: user
  contexts:
    web:
      place: web::connected::issues
- text: Read and explain contradictory task facts
  kind: product
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Due date
    - Tags
    - Estimate
    - Native duration
  actor: user
  contexts:
    web:
      place: web::connected::issues
references:
- kind: code
  role: implementation
  target: src/domain/conflicts.ts
- kind: code
  role: implementation
  target: src/components/overlays/Issues.tsx
---

# Read contradictory task facts

## Trigger

The person opens Things to settle.

## Outcome

The app presents date plus week label, multiple or invalid estimate tags, quick tasks over five minutes, or competing parent/child estimates where applicable. Native/tag mismatch is flagged in duration mode only.

## Edge cases

- Fully estimated open children supply the parent’s sum automatically and are not a competing-estimate conflict.
- Missing estimates are work to fill in, not errors.
