---
kind: primary
routes:
  web: Demo
steps:
- text: Start the tour
  kind: actor
  entities: []
  actor: visitor
  contexts:
    web:
      place: web::public::tour
- text: Present demonstration tasks
  kind: product
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
  actor: visitor
  contexts:
    web:
      place: web::public::tour
- text: Finish or leave the tour
  kind: actor
  entities: []
  actor: visitor
  contexts:
    web:
      place: web::public::tour
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
  actor: visitor
  contexts:
    web:
      place: web::public::tour
references:
- kind: code
  role: implementation
  target: src/components/overlays/Tour.tsx
- kind: code
  role: implementation
  target: src/store/preferences.ts
---

# Finish a tour and return to work in the demo

## Trigger

The person starts or replays the guided tour. The visitor is using the disposable demo.

## Outcome

Finishing, skipping, closing or leaving the tour restores the original workspace and retains any preference changes deliberately made during the tour.
