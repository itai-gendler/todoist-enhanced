---
kind: validation
routes:
  web: Demo
steps:
- text: Choose a project parent
  kind: actor
  entities:
  - entity: project
    effect: reads
    facts:
    - Name
    - Parent
  actor: visitor
  contexts:
    web:
      place: web::public::project
- text: The project nesting choice is invalid
  kind: condition
  entities:
  - entity: project
    effect: reads
    facts:
    - Workspace
    - Parent
  contexts:
    web:
      place: web::public::project
references:
- kind: code
  role: implementation
  target: src/store/structure.ts
- kind: code
  role: implementation
  target: src/components/ProjectMenu.tsx
---

# Keep invalid project nesting unchanged in the demo

## Trigger

The requested parent is in another workspace or would create a cycle. The visitor is using the disposable demo.

## Outcome

The app does not submit the nesting change.
