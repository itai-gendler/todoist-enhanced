---
kind: primary
result: achieved
routes:
  web: Demo
steps:
- text: Choose to add a division at this position
  kind: actor
  actor: visitor
  capability: create-section
  entities: []
  contexts:
    web:
      place: web::public::project
- text: Create the untitled section and start editing its name
  kind: product
  actor: visitor
  capability: create-section
  entities:
  - entity: section
    effect: creates
    facts:
    - Name
    - Description
    - Project
    - Order
    to: Active
  contexts:
    web:
      place: web::public::project
- text: Enter the section name
  kind: actor
  actor: visitor
  capability: edit-section
  entities:
  - entity: section
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::public::project
- text: Save the section name
  kind: product
  actor: visitor
  capability: edit-section
  entities:
  - entity: section
    effect: changes
    facts:
    - Name
  contexts:
    web:
      place: web::public::project
references:
- kind: code
  role: implementation
  target: src/views/ProjectView.tsx
- kind: code
  role: implementation
  target: src/store/structure.ts
---

# Name a new section in the demo

## Trigger

The person adds a section without a name.

## Outcome

The new section holds the entered name at the chosen position.
