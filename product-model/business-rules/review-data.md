---
appliesTo:
- type: capability
  id: run-review
- type: capability
  id: schedule-task
- type: capability
  id: edit-task
references:
- kind: code
  role: implementation
  target: src/domain/review.ts
- kind: code
  role: implementation
  target: src/views/ReviewView.tsx
---

# Review decisions change work without creating a review record

The daily pass estimates overdue and today’s work. The weekly pass also estimates undated weekly commitments. Review progress and choices are temporary; saved edits affect the underlying tasks. The mail step is only an outbound link to an external mail client.
