---
kind: primary
routes:
  web: Connected account
steps:
- text: The User chooses Duplicate on the section
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
- text: The Product creates a copy of the section below it, with copies of its open tasks and their subtasks
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
  - entity: task
    effect: creates
    facts:
    - Title
    - Description
    - Priority
    - Due date
    - Repeat rule
    - Deadline
    - Tags
    - Estimate
    - Native duration
    - Project
    - Section
    - Parent
    - Assignee
    - Order
    - Created on
    - Completed on
    - Kept on
    - Completable
    to: Open
    with: section
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

# Duplicate section

## Trigger

The User chooses Duplicate on a section.

## Outcome

A copy of the section appears just below it, holding copies of its open tasks with their subtasks.
