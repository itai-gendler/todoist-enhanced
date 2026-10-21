---
kind: validation
routes:
  web: Connected account
steps:
- kind: actor
  actor: user
  text: The User opens a task
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Assignee
  contexts: &id001
    web:
      place: web::connected::task
- kind: condition
  text: The containing project reports assignment unavailable.
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Assignee
  - entity: project
    effect: reads
    facts:
    - Assignment allowed
  contexts: *id001
- kind: product
  actor: user
  text: The assignment control is absent and the existing assignee is unchanged.
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Assignee
  contexts: *id001
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

# Read work when assignment is unavailable

## Trigger

The containing project reports assignment unavailable.

## Outcome

The assignment control is absent and the existing assignee is unchanged.
