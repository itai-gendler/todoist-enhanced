---
appliesTo:
- type: capability
  id: browse-week
- type: capability
  id: browse-today
- type: capability
  id: run-review
references:
- kind: code
  role: implementation
  target: src/domain/load.ts#summariseLoad
- kind: code
  role: implementation
  target: src/domain/load.ts#weeklyCapacity
- kind: code
  role: implementation
  target: src/views/WeekView.tsx
---

# Load describes the selected work and its applicable capacity

Displayed estimated minutes are divided by the applicable positive capacity and rounded to a percentage; unknown estimates are counted separately. Today uses that weekday’s capacity. My week uses a positive weekly override or the sum of all seven daily capacities. A view without meaningful capacity has no percentage.
