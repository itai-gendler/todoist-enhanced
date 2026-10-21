---
kind: primary
routes:
  web: Connected account
steps:
- text: The User picks an assignee for the task
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
- text: The Product assigns the task to the chosen person from its project
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

# Assign task

## Trigger

The User chooses an assignee for a task in a shared project.

## Outcome

The task shows its new assignee. The people offered are the User and the active collaborators of the task’s project; pending invitations are not offered.
