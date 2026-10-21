---
appliesTo:
- type: capability
  id: sync-work
- type: capability
  id: create-task
- type: capability
  id: edit-task
- type: capability
  id: share-project
- type: capability
  id: add-comment
- type: capability
  id: add-reaction
- type: capability
  id: nest-task
references:
- kind: code
  role: implementation
  target: src/store/sync.ts
- kind: code
  role: implementation
  target: src/store/tasks.ts
- kind: code
  role: implementation
  target: src/store/tasks-move.ts
- kind: code
  role: implementation
  target: src/components/CommentThread.tsx
---

# Local changes do not guarantee external acceptance

Task and structure edits appear optimistically and enter a local outbox. Network failures keep them pending; explicit refusals reverse the affected local changes and are reported. Requests grouped into one batch are not claimed to be an atomic Todoist transaction. Direct uploads and comment reactions have their own failure paths.
