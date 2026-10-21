---
kind: primary
routes:
  web: Demo
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
  actor: visitor
  contexts:
    web:
      place: web::public::task
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

# Save task fields in the demo

## Trigger

The person edits a task. The visitor is using the disposable demo.

## Outcome

The selected text, description, priority or deadline changes are saved. Checklist marks change their description line while preserving the other text. Changes affect demonstration work only; no request is sent to Todoist.

## Edge cases

- A checklist is description text; checking one does not complete a separate task.
- Task description input is limited to 16,383 characters.
