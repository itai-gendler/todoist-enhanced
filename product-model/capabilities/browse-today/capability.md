---
availability:
- place: web::connected
- place: web::public
references:
- kind: code
  role: implementation
  target: src/views/WeekView.tsx
- kind: code
  role: implementation
  target: src/domain/load.ts
---

# Browse Today

Read overdue tasks and tasks due today, measured against the current weekday’s capacity.
