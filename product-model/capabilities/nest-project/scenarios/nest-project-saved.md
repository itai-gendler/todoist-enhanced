---
kind: primary
routes:
  web: Connected account
steps:
- text: The User chooses a parent for the project
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
- text: The Product places the project under the chosen project or folder
  kind: product
  entities:
  - entity: project
    effect: changes
    facts:
    - Parent
    - Order
  - entity: folder
    effect: reads
    facts:
    - Name
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

# Nest project

## Trigger

The User drags a project a little to the right under another, or chooses a parent for it.

## Outcome

The project is nested under the chosen project or folder, in the same workspace.
