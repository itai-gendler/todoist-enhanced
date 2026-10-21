---
kind: primary
routes:
  web: Connected account
steps:
- text: The User changes the week label, the Quick or Gathering dust groups, the quiet delay or the estimate storage
  kind: actor
  entities:
  - entity: settings
    effect: reads
    facts:
    - Week label
  actor: user
  contexts:
    web:
      place: web::connected::features
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
  actor: user
  contexts:
    web:
      place: web::connected::features
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

# Change Features and planning settings

## Trigger

The User changes a setting in Features and planning.

## Outcome

The planning pages follow the new choices. Choosing another estimate storage decides where new estimates are written and converts nothing already saved.
