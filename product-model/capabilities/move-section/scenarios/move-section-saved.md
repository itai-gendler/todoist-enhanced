---
kind: primary
routes:
  web: Connected account
steps:
- text: The User chooses another destination for the section
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
- text: The Product moves the section with its tasks to the end of the chosen project
  kind: product
  entities:
  - entity: section
    effect: changes
    facts:
    - Project
    - Order
  - entity: task
    effect: changes
    facts:
    - Project
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

# Move section

## Trigger

The User moves a section to another project.

## Outcome

The section and its tasks appear at the end of the other project.
