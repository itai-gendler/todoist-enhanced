---
kind: primary
routes:
  web: Connected account
steps:
- text: The User chooses Undo after archiving the section
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
- text: The Product unarchives the section
  kind: product
  entities:
  - entity: section
    effect: changes
    facts: []
    from: Archived
    to: Active
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

# Restore section

## Trigger

The User has just archived a section and chooses Undo in the message.

## Outcome

The section is active in its project again.
