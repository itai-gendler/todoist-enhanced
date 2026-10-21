---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor chooses Duplicate on the section
  kind: actor
  entities:
  - entity: section
    effect: reads
    facts:
    - Name
  actor: visitor
  contexts:
    web:
      place: web::public::project
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
  actor: visitor
  contexts:
    web:
      place: web::public::project
references:
- kind: code
  role: implementation
  target: src/store/structure.ts
- kind: code
  role: implementation
  target: src/components/SectionMenu.tsx
---

# Duplicate section in the demo

## Trigger

The Visitor chooses Duplicate on a section. The visitor is using the disposable demo.

## Outcome

A copy of the section appears just below it, holding copies of its open tasks with their subtasks. Changes affect demonstration work only; no request is sent to Todoist.
