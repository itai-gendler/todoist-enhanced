---
availability:
- place: web::connected
- place: web::public
references:
- kind: code
  role: implementation
  target: src/domain/dnd.ts
- kind: code
  role: implementation
  target: src/store/tasks-move.ts
- kind: code
  role: implementation
  target: src/views/WeekView.tsx
- kind: code
  role: implementation
  target: src/store/calendar.ts
---

# Schedule task

Give work a date, commit it to anytime this week, or return it to Someday. The same destination meanings apply in lists, reviews and bulk actions.
