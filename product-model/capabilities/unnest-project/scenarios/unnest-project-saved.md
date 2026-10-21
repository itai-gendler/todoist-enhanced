---
kind: primary
routes:
  web: Connected account
steps:
- text: The User moves the nested project to the top level
  kind: actor
  entities:
  - entity: project
    effect: reads
    facts:
    - Inbox
  actor: user
  contexts:
    web:
      place: web::connected::project
- text: The Product takes the project out of its parent, at the top level of its workspace
  kind: product
  entities:
  - entity: project
    effect: changes
    facts:
    - Parent
    - Order
  - entity: workspace
    effect: reads
    facts:
    - Name
  actor: user
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

# Move project to top level

## Trigger

The User moves a nested project to the top level.

## Outcome

The project is no longer nested and sits at the top level of its space.
