---
kind: primary
routes:
  web: Connected account
steps:
- text: The User removes the task’s assignee
  kind: actor
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
  actor: user
  contexts:
    web:
      place: web::connected::task
- text: The Product clears the assignee of the task in its project
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Assignee
  - entity: project
    effect: reads
    facts:
    - Name
  actor: user
  contexts:
    web:
      place: web::connected::task
references:
- kind: code
  role: implementation
  target: src/domain/assignees.ts
- kind: code
  role: implementation
  target: src/domain/sharing.ts
- kind: code
  role: implementation
  target: src/store/collab.ts
- kind: code
  role: implementation
  target: src/components/AssigneeField.tsx
---

# Unassign task

## Trigger

The User removes the assignee of a task.

## Outcome

The task has no assignee.
