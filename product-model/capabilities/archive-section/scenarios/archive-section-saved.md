---
kind: primary
routes:
  web: Connected account
steps:
- text: The User confirms archiving the section
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
- text: The Product archives the section and offers Undo
  kind: product
  entities:
  - entity: section
    effect: changes
    facts: []
    from: Active
    to: Archived
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

# Archive section

## Trigger

The User chooses Archive on a section and confirms.

## Outcome

The section and its tasks leave the project’s page, and Todoist keeps the section among the project’s archived ones. Undo in the message brings it back.
