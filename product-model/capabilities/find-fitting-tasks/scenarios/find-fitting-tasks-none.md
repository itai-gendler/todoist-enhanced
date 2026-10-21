---
kind: alternate
routes:
  web: Connected account
steps:
- text: Choose available minutes
  kind: actor
  entities: []
  actor: user
  contexts:
    web:
      place: web::connected::time
- text: Separate unestimated tasks from tasks that exceed the duration
  kind: product
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Estimate
    - Due date
    - Tags
  actor: user
  contexts:
    web:
      place: web::connected::time
references:
- kind: code
  role: implementation
  target: src/components/TimePanel.tsx
- kind: code
  role: implementation
  target: src/domain/fits.ts
---

# Show what is missing when nothing fits

## Trigger

No eligible task fits the chosen duration.

## Outcome

The panel identifies work without estimates and suggests the next duration that could find work, when one exists.
