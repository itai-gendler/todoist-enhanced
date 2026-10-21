---
kind: primary
routes:
  web: Connected account
steps:
- text: The User adds a section at a chosen position
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
- text: The Product creates the section at that position in the project
  kind: product
  entities:
  - entity: section
    effect: creates
    facts:
    - Name
    - Description
    - Project
    - Order
    to: Active
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

# Create section

## Trigger

The User adds a section between two others, or at the end of a project.

## Outcome

The new section appears where it was added; without a name it starts with a placeholder name, ready to edit.
