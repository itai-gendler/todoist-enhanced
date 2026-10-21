---
availability:
- place: web::connected
- place: web::public
references:
- kind: code
  role: implementation
  target: src/components/CalendarSurface.tsx
- kind: code
  role: implementation
  target: src/store/calendar.ts
- kind: code
  role: implementation
  target: src/domain/calendar.ts
---

# Resize calendar task

Change a scheduled task’s estimated length in 15-minute steps. The selected estimate storage determines the write; tag mode keeps native calendar duration independent.
