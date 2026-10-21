---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor moves the dashboard cards, or resets them
  kind: actor
  entities:
  - entity: settings
    effect: reads
    facts:
    - Dashboard arrangement
  actor: visitor
  contexts:
    web:
      place: web::public::insights
- text: The Product saves the card order and choices in the settings
  kind: product
  entities:
  - entity: settings
    effect: changes
    facts:
    - Dashboard arrangement
  actor: visitor
  contexts:
    web:
      place: web::public::insights
references:
- kind: code
  role: implementation
  target: src/views/InsightsView.tsx
- kind: code
  role: implementation
  target: src/components/DashboardDisplayMenu.tsx
- kind: code
  role: implementation
  target: src/domain/dashboard.ts
---

# Change dashboard settings in the demo

## Trigger

The Visitor chooses Edit layout on the dashboard, or Reset to default. The visitor is using the disposable demo.

## Outcome

The dashboard shows its cards in the chosen order; Reset to default puts them back. Changes affect demonstration work only; no request is sent to Todoist.
