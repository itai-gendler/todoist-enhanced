---
kind: primary
routes:
  web: Connected account
steps:
- text: The User changes the section’s name or description
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
- text: The Product saves the section
  kind: product
  entities:
  - entity: section
    effect: changes
    facts:
    - Name
    - Description
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

# Edit section

## Trigger

The User chooses Edit on a section.

## Outcome

The section shows its new name and description.
