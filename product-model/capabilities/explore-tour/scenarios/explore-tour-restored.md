---
kind: primary
routes:
  web: Connected account
steps:
- text: Start the tour
  kind: actor
  entities: []
  actor: user
  contexts:
    web:
      place: web::connected::tour
- text: Present demonstration tasks
  kind: product
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
  actor: user
  contexts:
    web:
      place: web::connected::tour
- text: Finish or leave the tour
  kind: actor
  entities: []
  actor: user
  contexts:
    web:
      place: web::connected::tour
- text: Restore the original tasks and settings
  kind: product
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
  - entity: settings
    effect: reads
    facts:
    - Setup completion
  actor: user
  contexts:
    web:
      place: web::connected::tour
references:
- kind: code
  role: implementation
  target: src/components/overlays/Tour.tsx
- kind: code
  role: implementation
  target: src/store/preferences.ts
---

# Finish a tour and return to work

## Trigger

The person starts or replays the guided tour.

## Outcome

Finishing, skipping, closing or leaving the tour restores the original workspace and retains any preference changes deliberately made during the tour.
