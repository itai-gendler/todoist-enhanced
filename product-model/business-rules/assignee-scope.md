---
appliesTo:
- type: entity
  id: display-preferences
  facts:
  - Filters
- type: entity
  id: task
  facts:
  - Assignee
  - Estimate
references:
- kind: code
  role: implementation
  target: src/domain/types.ts
- kind: code
  role: implementation
  target: src/hooks/useData.ts#useData
- kind: code
  role: implementation
  target: src/domain/assignees.ts
---

# Personal planning defaults to mine and unassigned work

Personal planning pages default to the current person’s assignments and unassigned work; project and saved-query pages default to everyone. The selected assignee scope applies to the child index before rollups and load are calculated, so totals follow the selected work.
