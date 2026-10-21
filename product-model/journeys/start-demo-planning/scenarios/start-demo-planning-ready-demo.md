---
kind: primary
result: achieved
routes:
  web: Demo
steps:
- text: Choose Explore with demo data
  kind: actor
  actor: visitor
  capability: explore-demo
  entities: []
  contexts:
    web:
      place: web::public::connect
- text: Load fictional work and offer setup
  kind: product
  actor: visitor
  capability: explore-demo
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
    facts: &id001
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
  contexts:
    web:
      place: web::public::setup
- text: Choose first-run preferences
  kind: actor
  actor: visitor
  capability: complete-setup
  entities: []
  contexts:
    web:
      place: web::public::setup
- text: Save the setup choices
  kind: product
  actor: visitor
  capability: complete-setup
  entities:
  - entity: settings
    effect: changes
    facts: *id001
  contexts:
    web:
      place: web::public::setup
references:
- kind: code
  role: implementation
  target: src/App.tsx
- kind: code
  role: implementation
  target: src/store/sync.ts
- kind: code
  role: implementation
  target: src/components/overlays/Walkthrough.tsx
---

# Start planning in the demo in the demo

## Trigger

A visitor chooses demo exploration.

## Outcome

The visitor has completed Setup and can plan with the supplied demonstration work.
