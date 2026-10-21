---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor changes the week label, the Quick or Gathering dust groups, the quiet delay or the estimate storage
  kind: actor
  entities:
  - entity: settings
    effect: reads
    facts:
    - Week label
  actor: visitor
  contexts:
    web:
      place: web::public::features
- text: The Product saves the choices in the settings without converting any estimate
  kind: product
  entities:
  - entity: settings
    effect: changes
    facts:
    - Week label
    - Quick group
    - Dust group
    - Dust delay
    - Quiet delay
    - Daily capacity
    - Weekly override
    - Estimate storage
  - entity: account
    effect: reads
    facts:
    - Name
  actor: visitor
  contexts:
    web:
      place: web::public::features
references:
- kind: code
  role: implementation
  target: src/views/SettingsView.tsx
- kind: code
  role: implementation
  target: src/store/preferences.ts
- kind: code
  role: implementation
  target: src/store/prefs.ts
---

# Change Features and planning settings in the demo

## Trigger

The Visitor changes a setting in Features and planning. The visitor is using the disposable demo.

## Outcome

The planning pages follow the new choices. Choosing another estimate storage decides where new estimates are written and converts nothing already saved. Changes affect demonstration work only; no request is sent to Todoist.
