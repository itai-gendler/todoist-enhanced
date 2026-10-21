---
kind: primary
routes:
  web: Connected account
steps:
- text: The User drags the section to a new place among the sections
  kind: actor
  entities:
  - entity: section
    effect: reads
    facts:
    - Name
  actor: user
  contexts:
    web:
      place: web::connected::project
- text: The Product saves the section’s place among the project’s active sections
  kind: product
  entities:
  - entity: section
    effect: changes
    facts:
    - Order
  - entity: project
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
  target: src/components/SectionMenu.tsx
---

# Reorder section

## Trigger

The User drags a section to a new place.

## Outcome

The section sits at its new place among the project’s active sections.
