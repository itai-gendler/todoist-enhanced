---
appliesTo:
- type: entity
  id: task
  facts:
  - Created on
  - Kept on
  - Due date
  - Tags
references:
- kind: code
  role: implementation
  target: src/domain/views.ts#splitDust
- kind: code
  role: implementation
  target: src/domain/views.ts#monthsAreUp
- kind: code
  role: implementation
  target: src/store/dust.ts
---

# Gathering dust uses creation age and the last Keep day

Open top-level Someday work is old on its configured calendar-month anniversary from creation. Missing creation dates are excluded. Keeping a task postpones its return for another full delay from the local Keep day; quick grouping takes precedence when enabled. The available delays are 1, 2, 3, 6 and 12 months.
