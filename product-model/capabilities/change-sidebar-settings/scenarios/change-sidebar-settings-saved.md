---
kind: primary
routes:
  web: Connected account
steps:
- text: The User chooses which entries and counts the sidebar shows, and their order
  kind: actor
  entities:
  - entity: settings
    effect: reads
    facts:
    - Sidebar
  actor: user
  contexts:
    web:
      place: web::connected::sidebar
- text: The Product saves the Sidebar settings
  kind: product
  entities:
  - entity: settings
    effect: changes
    facts:
    - Sidebar
  actor: user
  contexts:
    web:
      place: web::connected::sidebar
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

# Change Sidebar settings

## Trigger

The User changes a setting in Sidebar.

## Outcome

The sidebar shows the chosen entries and counts in the chosen order.
