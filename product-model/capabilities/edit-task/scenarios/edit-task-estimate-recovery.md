---
kind: edge
routes:
  web: Connected account
steps:
- text: The User saves an estimate while estimates are stored as native durations
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
- text: The Product requests the duration as native minutes
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
- text: Todoist does not keep the requested duration
  kind: condition
  entities: []
  contexts:
    web:
      place: web::connected::task
- text: The Product switches estimate storage back to tags in the settings and writes the estimate as a tag
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Estimate
    - Tags
  - entity: settings
    effect: changes
    facts:
    - Estimate storage
  - entity: tag
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

# Recover a native estimate as tags

## Trigger

Todoist drops or refuses the requested native duration.

## Outcome

The app switches estimate storage back to tags, writes the intended estimate as a tag and explains the fallback; any native calendar block returned by Todoist is preserved.

## Edge cases

- If server read-back is unavailable, the write remains pending for later verification.
- Unrelated validation failures use the ordinary refusal path.
