---
appliesTo:
- type: entity
  id: task
  facts:
  - Estimate
  - Tags
  - Due date
references:
- kind: code
  role: implementation
  target: src/domain/views.ts#isQuick
- kind: code
  role: implementation
  target: src/domain/views.ts#splitQuick
---

# Quick work takes at most five estimated minutes

An estimate above five minutes excludes work from Quick even when tagged quick. Without an estimate, quick is the available claim. My week keeps late work in Behind schedule and groups only today’s quick work; project, tag, Inbox and Someday group open top-level quick work that is overdue, today or undated. Each task is listed once.
