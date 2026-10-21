---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor opens the task
  kind: actor
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
  actor: visitor
  contexts:
    web:
      place: web::public::task
- text: The Product shows the task with its subtasks and checklist
  kind: product
  entities:
  - entity: task
    effect: reads
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
  - entity: tag
    effect: reads
    facts:
    - Name
    - Colour
    - Favourite
    - Order
    - Reserved
  actor: visitor
  contexts:
    web:
      place: web::public::task
references:
- kind: code
  role: implementation
  target: src/components/overlays/TaskDetail.tsx
- kind: code
  role: implementation
  target: src/store/tasks.ts
---

# Browse task in the demo

## Trigger

The Visitor opens a task from any list. The visitor is using the disposable demo.

## Outcome

The task panel shows the task’s fields, its description with checklist progress such as “3 of 7”, and its subtasks.

## Edge cases

- An empty selection is shown as no matching work; the product does not invent tasks.
