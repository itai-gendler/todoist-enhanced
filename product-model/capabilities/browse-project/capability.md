---
availability:
- place: web::connected
- place: web::public
references:
- kind: code
  role: implementation
  target: src/views/ProjectView.tsx
- kind: code
  role: implementation
  target: src/store/selectors.ts
- kind: code
  role: implementation
  target: src/hooks/useProjectCompleted.ts
domain: projects
---

# Browse project

Read a project or the Inbox, its sections, subtasks and optionally completed work. Existing workspaces and folders provide the project grouping.
