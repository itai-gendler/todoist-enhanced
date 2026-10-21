---
entities:
- entity: task
  shows:
  - Title
  - Due date
  - Tags
  - Estimate
  - Native duration
- entity: notification
  shows:
  - Message
  - Sender
  - Subject
  - Received on
  - Read
  - Invitation answer
  - Answer available
references:
- kind: code
  role: implementation
  target: src/components/overlays/Issues.tsx
---

# Things to settle

Read contradictions and Todoist notices, and decide what to do about them. This context uses disposable demonstration work.
