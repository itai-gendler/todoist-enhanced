---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor opens the Account page
  kind: actor
  entities:
  - entity: account
    effect: reads
    facts:
    - Name
  actor: visitor
  contexts:
    web:
      place: web::public::account
- text: The Product shows the fictional account’s profile and week start
  kind: product
  entities:
  - entity: account
    effect: reads
    facts:
    - Name
    - Email
    - Week start
    - Connection method
    - Sync status
    - Pending changes
  actor: visitor
  contexts:
    web:
      place: web::public::account
references:
- kind: code
  role: implementation
  target: src/views/SettingsView.tsx
---

# Browse account in the demo

## Trigger

The Visitor opens Account in Settings. The visitor is using the disposable demo.

## Outcome

The fictional account’s name, email and week start are shown.
