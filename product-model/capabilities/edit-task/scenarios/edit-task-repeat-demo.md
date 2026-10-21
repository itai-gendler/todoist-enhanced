---
kind: alternate
routes:
  web: Demo
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
  actor: visitor
  contexts:
    web:
      place: web::public::task
- text: Save the demonstration task repeat details locally
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Repeat rule
    - Due date
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

# Save a repeat rule in the demo

## Trigger

The person specifies a repeat rule or edits its time. The visitor is using the disposable demo.

## Outcome

The app stores the demonstration recurrence text and known first day locally. Changes affect demonstration work only; no request is sent to Todoist.

## Edge cases

- The demonstration does not establish the external recurrence grammar.
