---
kind: primary
routes:
  web: Connected account
steps:
- text: Enter task fields
  kind: actor
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
  actor: user
  contexts:
    web:
      place: web::connected::task
- text: Create the open task with supplied values and defaults
  kind: product
  entities:
  - entity: task
    effect: creates
    facts:
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
    to: Open
  actor: user
  contexts:
    web:
      place: web::connected::task
references:
- kind: code
  role: implementation
  target: src/components/overlays/Composer.tsx
- kind: code
  role: implementation
  target: src/domain/shorthand.ts
- kind: code
  role: implementation
  target: src/store/tasks.ts
- kind: code
  role: implementation
  target: src/domain/dnd.ts
---

# Capture a task

## Trigger

The person opens the composer and supplies a nonempty task name.

## Outcome

A new open task uses the selected fields; inline subtasks are created with it. Recurring input is submitted for Todoist to resolve.

## Edge cases

- Blank parsed content is not submitted.
- A task created from My week starts with the configured week label; a day, project or section supplies its own context.
- Subtask project shorthand stays text because the subtask belongs to its parent’s project.
- Rejected shorthand can be retained as literal title text.
