---
kind: validation
routes:
  web: Connected account
steps:
- text: Choose a project parent
  kind: actor
  entities:
  - entity: project
    effect: reads
    facts:
    - Name
    - Parent
  actor: user
  contexts:
    web:
      place: web::connected::project
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
      place: web::connected::project
references:
- kind: code
  role: implementation
  target: src/store/structure.ts
- kind: code
  role: implementation
  target: src/components/ProjectMenu.tsx
---

# Keep invalid project nesting unchanged

## Trigger

The requested parent is in another workspace or would create a cycle.

## Outcome

The app does not submit the nesting change.
