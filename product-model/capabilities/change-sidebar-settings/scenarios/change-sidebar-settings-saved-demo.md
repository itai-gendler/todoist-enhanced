---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor chooses which entries and counts the sidebar shows, and their order
  kind: actor
  entities:
  - entity: settings
    effect: reads
    facts:
    - Sidebar
  actor: visitor
  contexts:
    web:
      place: web::public::sidebar
- text: The Product saves the Sidebar settings
  kind: product
  entities:
  - entity: settings
    effect: changes
    facts:
    - Sidebar
  actor: visitor
  contexts:
    web:
      place: web::public::sidebar
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

# Change Sidebar settings in the demo

## Trigger

The Visitor changes a setting in Sidebar. The visitor is using the disposable demo.

## Outcome

The sidebar shows the chosen entries and counts in the chosen order. Changes affect demonstration work only; no request is sent to Todoist.
