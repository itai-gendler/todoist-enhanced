---
kind: primary
routes:
  web: Demo
steps:
- text: Open a filter
  kind: actor
  entities:
  - entity: filter
    effect: reads
    facts:
    - Name
    - Query
  actor: visitor
  contexts:
    web:
      place: web::public::filter
- text: Read matching tasks for the filter
  kind: product
  entities:
  - entity: filter
    effect: reads
    facts:
    - Query
  - entity: task
    effect: reads
    facts:
    - Title
    - Due date
    - Priority
    - Tags
    - Completed on
  actor: visitor
  contexts:
    web:
      place: web::public::filter
references:
- kind: code
  role: implementation
  target: src/hooks/useFilterResult.ts
- kind: code
  role: implementation
  target: src/api/filters.ts
- kind: code
  role: implementation
  target: src/views/SimpleListView.tsx
---

# Read saved query matches in the demo

## Trigger

The person opens a saved filter. The visitor is using the disposable demo.

## Outcome

Each top-level query part has its own result list. Display filters refine the returned work; calendar completion inclusion retains locally completed matches.

## Edge cases

- Newly authored demo queries have no live evaluation; supplied examples use the demo’s fixed matching logic.
