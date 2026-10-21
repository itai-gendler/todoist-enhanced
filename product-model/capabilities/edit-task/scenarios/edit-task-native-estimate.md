---
kind: alternate
routes:
  web: Connected account
steps:
- text: Enter the task estimate
  kind: actor
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Estimate
  actor: user
  contexts:
    web:
      place: web::connected::task
- text: Request the native task estimate
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Estimate
    - Tags
    - Native duration
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

# Save a native estimate

## Trigger

Native duration is selected and the account is eligible to request it.

## Outcome

The estimate is requested as a minute duration and estimate tags are removed. The app checks returned or fetched server data before considering the native write verified.
