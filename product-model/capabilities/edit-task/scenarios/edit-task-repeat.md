---
kind: alternate
routes:
  web: Connected account
steps:
- text: Edit the task repeat rule
  kind: actor
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Repeat rule
    - Due date
  actor: user
  contexts:
    web:
      place: web::connected::task
- text: Submit and reconcile the task repeat details
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Repeat rule
    - Due date
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

# Save a repeat rule

## Trigger

The person specifies a repeat rule or edits its time.

## Outcome

The app submits the recurrence text and language, including a known first day where appropriate, and adopts Todoist’s resolved date.

## Edge cases

- Locally shown provisional dates are replaced by the external result; the app does not guarantee the external recurrence grammar.
