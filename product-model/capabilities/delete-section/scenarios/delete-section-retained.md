---
kind: primary
routes:
  web: Connected account
steps:
- text: Confirm deletion of the section
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
- text: Move tasks out of the section
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Section
  - entity: section
    effect: reads
    facts:
    - Project
  actor: user
  contexts:
    web:
      place: web::connected::project
- text: Remove the empty section
  kind: product
  entities:
  - entity: section
    effect: removes
    from: Active
  actor: user
  contexts:
    web:
      place: web::connected::project
references:
- kind: code
  role: implementation
  target: src/components/SectionMenu.tsx
- kind: code
  role: implementation
  target: src/store/structure.ts
---

# Delete a section and retain its tasks

## Trigger

The person confirms deletion of a section.

## Outcome

The app requests moves for the contained work before deleting the section; tasks remain at the project root when those requests succeed.
