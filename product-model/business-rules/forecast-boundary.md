---
appliesTo:
- type: capability
  id: browse-upcoming
- type: capability
  id: resize-task
- type: capability
  id: schedule-task
references:
- kind: code
  role: implementation
  target: src/domain/projectOccurrences.ts
- kind: code
  role: implementation
  target: src/components/CalendarSurface.tsx
- kind: code
  role: implementation
  target: src/store/calendar.ts
---

# Forecasts never create or mutate saved tasks

Future occurrences are read-only projections of supported repeat rules. Unsupported, completion-relative and different-timezone rules are not invented. Opening a projection reaches its real source task; completing or rescheduling work acts on real tasks only.
