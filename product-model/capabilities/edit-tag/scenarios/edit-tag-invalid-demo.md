---
kind: validation
routes:
  web: Demo
steps:
- text: Enter a tag name
  kind: actor
  entities:
  - entity: tag
    effect: reads
    facts:
    - Name
  actor: visitor
  contexts:
    web:
      place: web::public::tags
- text: Reject the rename without changing the tag
  kind: product
  entities:
  - entity: tag
    effect: reads
    facts:
    - Name
    - Reserved
  actor: visitor
  contexts:
    web:
      place: web::public::tags
references:
- kind: code
  role: implementation
  target: src/store/structure.ts
- kind: code
  role: implementation
  target: src/components/overlays/TagSheet.tsx
---

# Keep a rejected tag name unchanged in the demo

## Trigger

The proposed name is empty, duplicates another tag, or involves a reserved system name. The visitor is using the disposable demo.

## Outcome

The app explains the rejected rename and preserves the previous tag and task references.
