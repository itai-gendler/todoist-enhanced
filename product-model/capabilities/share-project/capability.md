---
availability:
- place: web::connected
references:
- kind: code
  role: implementation
  target: src/components/overlays/ShareSheet.tsx
- kind: code
  role: implementation
  target: src/store/collab.ts
domain: projects
---

# Share project

Submit an invitation by email and refresh the project’s returned member list. Workspace invitations may request Collaborator or Admin; personal invitations carry no role selection.
