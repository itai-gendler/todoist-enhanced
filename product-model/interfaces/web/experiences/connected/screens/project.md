---
entities:
- entity: project
  shows:
  - Inbox
  - Name
  - Description
  - Colour
  - Favourite
  - Workspace
  - Parent
  - Order
  - Access
  - My role
  - Access editing available
  - People management available
  - Assignment allowed
  - Shared with me
  - Default view
- entity: section
  shows:
  - Name
  - Description
  - Project
  - Order
- entity: task
  shows:
  - Title
  - Description
  - Due date
  - Repeat rule
  - Estimate
  - Tags
  - Priority
  - Project
  - Section
  - Parent
  - Assignee
  - Completed on
- entity: project-member
  shows:
  - Name
  - Email
  - Role
  - Participation
- entity: workspace
  shows:
  - Name
  - Default access
- entity: folder
  shows:
  - Name
  - Workspace
  - Order
  - Expanded
references:
- kind: code
  role: implementation
  target: src/views/ProjectView.tsx
entryPoints:
- web: '#/project/{project}'
---

# Project

Read and change a selected project, its sections, work and people. The Inbox uses this same working context.
