---
availability:
- place: web::connected
references:
- kind: code
  role: implementation
  target: src/domain/sharing.ts
- kind: code
  role: implementation
  target: src/store/collab.ts
- kind: code
  role: implementation
  target: src/components/overlays/ShareSheet.tsx
domain: projects
---

# Leave project

Leave a project another person created and shared, removing its work from this account at once; a refusal from Todoist brings it back.
