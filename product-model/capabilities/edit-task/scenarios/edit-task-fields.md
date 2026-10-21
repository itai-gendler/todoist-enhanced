---
kind: primary
routes:
  web: Connected account
steps:
- text: Edit task fields
  kind: actor
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Description
    - Priority
    - Deadline
  actor: user
  contexts:
    web:
      place: web::connected::task
- text: Save the changed task fields
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Title
    - Description
    - Priority
    - Deadline
  actor: user
  contexts:
    web:
      place: web::connected::task
references:
- kind: code
  role: implementation
  target: src/components/overlays/TaskDetail.tsx
- kind: code
  role: implementation
  target: src/components/Checklist.tsx
- kind: code
  role: implementation
  target: src/store/tasks.ts
- kind: code
  role: implementation
  target: src/domain/estimates.ts
- kind: code
  role: implementation
  target: src/store/estimate-safety.ts
- kind: code
  role: implementation
  target: src/components/overlays/Unestimated.tsx
---

# Save task fields

## Trigger

The person edits a task.

## Outcome

The selected text, description, priority or deadline changes are saved. Checklist marks change their description line while preserving the other text.

## Edge cases

- A checklist is description text; checking one does not complete a separate task.
- Task description input is limited to 16,383 characters.
