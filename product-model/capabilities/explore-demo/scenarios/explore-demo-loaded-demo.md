---
kind: primary
routes:
  web: Demo
steps:
- text: Choose demo exploration
  kind: actor
  entities: []
  actor: visitor
  contexts:
    web:
      place: web::public::connect
- text: Supply a fictional account and default settings
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
      place: web::public::setup
references:
- kind: code
  role: implementation
  target: src/store/sync.ts
- kind: code
  role: implementation
  target: src/demo/demoData.ts
---

# Explore a fictional workspace in the demo

## Trigger

The visitor chooses Explore with demo data. The visitor is using the disposable demo.

## Outcome

Demonstration work is available and first-run Setup can be shown. Changes affect demonstration work only; no request is sent to Todoist.
