---
kind: alternate
routes:
  web: Demo
steps:
- text: Choose available minutes
  kind: actor
  entities: []
  actor: visitor
  contexts:
    web:
      place: web::public::time
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
  actor: visitor
  contexts:
    web:
      place: web::public::time
references:
- kind: code
  role: implementation
  target: src/components/TimePanel.tsx
- kind: code
  role: implementation
  target: src/domain/fits.ts
---

# Show what is missing when nothing fits in the demo

## Trigger

No eligible task fits the chosen duration. The visitor is using the disposable demo.

## Outcome

The panel identifies work without estimates and suggests the next duration that could find work, when one exists.
