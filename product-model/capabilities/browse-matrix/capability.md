---
availability:
- place: web::connected
- place: web::public
references:
- kind: code
  role: implementation
  target: src/views/EisenhowerView.tsx
- kind: code
  role: implementation
  target: src/domain/eisenhower.ts
---

# Browse Eisenhower matrix

Read urgency and importance using the selected date buckets and priorities, with optional future and Someday work.
