---
appliesTo:
- type: entity
  id: task
  effect: changes
  facts:
  - Completed on
references:
- kind: code
  role: implementation
  target: src/store/tasks.ts
permits:
- actors:
  - user
  - visitor
  when:
  - fact: Completable
    is: true
---

# Users complete only tasks that support completion

Tasks beginning with the uncompletable marker have no completion action. One-off completion can be undone; recurring completion asks Todoist for the next occurrence.
