---
kind: primary
routes:
  web: Connected account
steps:
- text: The User answers the Setup steps and finishes
  kind: actor
  entities:
  - entity: settings
    effect: reads
    facts:
    - Language
  actor: user
  contexts:
    web:
      place: web::connected::setup
- text: The Product saves the first-run choices and records Setup as complete in the settings
  kind: product
  entities:
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
  actor: user
  contexts:
    web:
      place: web::connected::setup
references:
- kind: code
  role: implementation
  target: src/components/overlays/Walkthrough.tsx
- kind: code
  role: implementation
  target: src/store/preferences.ts
---

# Complete setup

## Trigger

Setup opens after connecting for the first time.

## Outcome

The chosen appearance, layout of Today and My week, sidebar, task details and estimate storage apply, and Setup is not shown again. Everything chosen stays changeable in Settings.
