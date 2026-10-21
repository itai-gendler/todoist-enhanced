---
appliesTo:
- type: entity
  id: task
  facts:
  - Due date
  - Tags
references:
- kind: code
  role: implementation
  target: src/domain/views.ts#bucketOf
- kind: code
  role: implementation
  target: src/domain/views.ts#groupWeek
- kind: code
  role: implementation
  target: src/domain/types.ts
---

# Dates take precedence over the weekly label

A real due date places work by date. Without a date, the configured week label means Anytime this week; neither means Someday. My week includes overdue, today and Anytime this week, not all future dates inside the current calendar week. Label matching is case-insensitive.
