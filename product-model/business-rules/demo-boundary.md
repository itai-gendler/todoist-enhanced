---
appliesTo:
- type: capability
  id: explore-demo
- type: capability
  id: explore-tour
- type: capability
  id: create-task
- type: capability
  id: edit-task
references:
- kind: code
  role: implementation
  target: src/store/sync.ts
---

# Demo mutations remain in the fictional workspace

Demo changes are neither sent to Todoist nor placed in its write queue. Reloading reconstructs demonstration work. A guided tour temporarily substitutes the demonstration workspace and restores the original on exit.
