---
kind: edge
routes:
  web: Demo
steps:
- text: Read future tasks
  kind: actor
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Repeat rule
  actor: visitor
  contexts:
    web:
      place: web::public::upcoming
- text: Show the real task without inventing future tasks
  kind: product
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Due date
    - Repeat rule
  actor: visitor
  contexts:
    web:
      place: web::public::upcoming
references:
- kind: code
  role: implementation
  target: src/views/UpcomingView.tsx
- kind: code
  role: implementation
  target: src/domain/projectOccurrences.ts
---

# Keep an opaque repeat rule as its current task in the demo

## Trigger

A repeating task has a completion-relative, unsupported or different-timezone rule. The visitor is using the disposable demo.

## Outcome

The current real task remains available, and the app indicates that some future occurrences cannot be forecast.
