---
kind: primary
routes:
  web: Connect
steps:
- text: Choose Todoist sign-in
  kind: actor
  entities: []
  actor: visitor
  contexts:
    web:
      place: web::public::connect
- text: Start the external consent round trip
  kind: product
  entities: []
  actor: visitor
  contexts:
    web:
      place: web::public::connect
- text: Complete the choice on Todoist’s consent page
  kind: actor
  entities: []
  actor: visitor
- text: Read the returned account and its settings
  kind: product
  entities:
  - entity: account
    effect: creates
    facts:
    - Name
    - Email
    - Week start
    - Plan
    - Duration storage allowed
    - Connection method
    - Sync status
    - Pending changes
  - entity: settings
    effect: changes
    facts:
    - Language
    - General
    - Appearance
    - Sidebar
    - Lists
    - Week label
    - Quick group
    - Dust group
    - Dust delay
    - Quiet delay
    - Daily capacity
    - Weekly override
    - Estimate storage
    - Conflict checks
    - Matrix rules
    - Dashboard arrangement
    - Setup completion
    - Release notices
  actor: visitor
  contexts:
    web:
      place: web::public::connect
references:
- kind: code
  role: implementation
  target: src/views/ConnectView.tsx
- kind: code
  role: implementation
  target: src/api/oauth.ts
- kind: code
  role: implementation
  target: src/api/auth.ts
- kind: code
  role: implementation
  target: src/store/sync.ts
---

# Connect through Todoist

## Trigger

The visitor chooses Continue with Todoist.

## Outcome

After a successful exchange and workspace read, the account is connected. New accounts are offered Setup; an existing destination is respected.
