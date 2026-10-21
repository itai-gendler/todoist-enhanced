---
availability:
- place: web::connected
- place: web::public
references:
- kind: code
  role: implementation
  target: src/views/ReviewView.tsx
- kind: code
  role: implementation
  target: src/domain/review.ts
---

# Run review

Walk a daily or weekly pass over existing work, acting on it in the review. The pass can be finished or abandoned without saving a separate review record.
