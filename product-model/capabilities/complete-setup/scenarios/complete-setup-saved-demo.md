---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor answers the Setup steps and finishes
  kind: actor
  entities:
  - entity: settings
    effect: reads
    facts:
    - Language
  actor: visitor
  contexts:
    web:
      place: web::public::setup
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
  actor: visitor
  contexts:
    web:
      place: web::public::setup
references:
- kind: code
  role: implementation
  target: src/components/overlays/Walkthrough.tsx
- kind: code
  role: implementation
  target: src/store/preferences.ts
---

# Complete setup in the demo

## Trigger

Setup opens when the demo starts. The visitor is using the disposable demo.

## Outcome

The chosen appearance, layout of Today and My week, sidebar, task details and estimate storage apply, and Setup is not shown again. Everything chosen stays changeable in Settings. Changes affect demonstration work only; no request is sent to Todoist.
