---
availability:
- place: web::connected
references:
- kind: code
  role: implementation
  target: src/domain/projectAccess.ts
- kind: code
  role: implementation
  target: src/components/overlays/ShareSheet.tsx
domain: projects
---

# Change project access

Request the chosen visibility for a project: Restricted or Public for personal projects, and also Team within a workspace. Unknown returned values stay visible.
