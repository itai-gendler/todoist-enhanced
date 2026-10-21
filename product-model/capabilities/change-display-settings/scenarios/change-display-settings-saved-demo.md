---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor changes the mode, grouping, sorting or inclusions of the page
  kind: actor
  entities:
  - entity: display-preferences
    effect: reads
    facts:
    - Page
  actor: visitor
  contexts:
    web:
      place: web::public::display
- text: The Product remembers these display preferences for the page
  kind: product
  entities:
  - entity: display-preferences
    effect: changes
    facts:
    - Page
    - Mode
    - Grouping
    - Sorting
    - Filters
    - Calendar
    - Table
  actor: visitor
  contexts:
    web:
      place: web::public::display
references:
- kind: code
  role: implementation
  target: src/components/DisplayMenu.tsx
- kind: code
  role: implementation
  target: src/components/TableColumnEditor.tsx
- kind: code
  role: implementation
  target: src/store/preferences.ts
- kind: code
  role: implementation
  target: src/store/prefs.ts
---

# Change Display settings in the demo

## Trigger

The Visitor changes the Display control on a task page. The visitor is using the disposable demo.

## Outcome

The page shows its tasks in the chosen mode, grouping, sorting and filters, remembered for that page. Changes affect demonstration work only; no request is sent to Todoist.
