---
availability:
- place: web::connected
- place: web::public
references:
- kind: code
  role: implementation
  target: src/components/TimePanel.tsx
- kind: code
  role: implementation
  target: src/domain/fits.ts
---

# Find tasks that fit

Find open top-level tasks whose counted duration fits the chosen minutes, in the current page or across open work.
