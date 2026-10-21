---
appliesTo:
- type: capability
  id: schedule-task
- type: capability
  id: create-task
- type: capability
  id: add-task-tag
references:
- kind: code
  role: implementation
  target: src/domain/dnd.ts
- kind: code
  role: implementation
  target: src/store/tasks-move.ts
---

# Each planning destination has one task meaning

Today or a specific day sets a date and removes the week label. Anytime this week clears the date and adds the configured week label. Someday clears the date and removes that label. A tag destination adds rather than replaces other tags.
