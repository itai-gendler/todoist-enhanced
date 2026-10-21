---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor chooses Duplicate on the task
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
- text: The Product creates an open copy of the task and of its open subtasks
  kind: product
  entities:
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
  actor: visitor
  contexts:
    web:
      place: web::public::task
references:
- kind: code
  role: implementation
  target: src/store/tasks.ts
---

# Duplicate task in the demo

## Trigger

The Visitor chooses Duplicate on a task. The visitor is using the disposable demo.

## Outcome

An open copy of the task appears with copies of its open subtasks; comments stay with the original. Changes affect demonstration work only; no request is sent to Todoist.
