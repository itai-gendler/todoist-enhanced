---
kind: primary
routes:
  web: Connected account
steps:
- text: The User chooses Archive on the project
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
- text: The Product archives the project
  kind: product
  entities:
  - entity: project
    effect: changes
    facts: []
    from: Active
    to: Archived
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

# Archive project

## Trigger

The User chooses Archive on a project.

## Outcome

The project is archived, not deleted, and leaves the project lists; a message names it.
