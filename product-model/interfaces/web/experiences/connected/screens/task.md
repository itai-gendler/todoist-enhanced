---
entities:
- entity: task
  shows:
  - Title
  - Description
  - Priority
  - Due date
  - Repeat rule
  - Deadline
  - Tags
  - Estimate
  - Native duration
  - Project
  - Section
  - Parent
  - Assignee
  - Order
  - Created on
  - Completed on
  - Kept on
  - Completable
- entity: tag
  shows:
  - Name
  - Colour
  - Favourite
  - Order
  - Reserved
- entity: comment
  shows:
  - Text
  - Posted on
  - Author
  - Attachment
  - Reactions
- entity: project-member
  shows:
  - Name
  - Email
  - Role
  - Participation
- entity: project
  shows:
  - Name
references:
- kind: code
  role: implementation
  target: src/components/overlays/TaskDetail.tsx
---

# Task

Create or inspect one task, its fields, subtasks, checklist and discussion.
