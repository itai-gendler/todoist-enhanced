---
kind: primary
routes:
  web: Connected account
steps:
- text: The User opens the Account page
  kind: actor
  entities:
  - entity: account
    effect: reads
    facts:
    - Name
  actor: user
  contexts:
    web:
      place: web::connected::account
- text: The Product shows the account’s profile, week start and connection status
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
  actor: user
  contexts:
    web:
      place: web::connected::account
references:
- kind: code
  role: implementation
  target: src/views/SettingsView.tsx
---

# Browse account

## Trigger

The User opens Account in Settings.

## Outcome

The account’s name, email and week start are shown with how it is connected, whether it is synchronized and how many changes are waiting. Managing the Todoist account itself happens in Todoist.
