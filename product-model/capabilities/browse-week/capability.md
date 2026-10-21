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
  target: src/domain/views.ts
- kind: code
  role: implementation
  target: src/domain/load.ts
- kind: code
  role: implementation
  target: src/store/selectors.ts
---

# Browse My week

Read overdue tasks, tasks due today and undated tasks carrying the configured week label, with estimates and weekly load.
