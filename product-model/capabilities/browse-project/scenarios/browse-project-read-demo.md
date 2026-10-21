---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor opens the project
  kind: actor
  entities:
  - entity: project
    effect: reads
    facts:
    - Name
  actor: visitor
  contexts:
    web:
      place: web::public::project
- text: The Product shows the project’s sections, tasks and subtasks
  kind: product
  entities:
  - entity: project
    effect: reads
    facts:
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
    effect: reads
    facts:
    - Name
    - Description
    - Project
    - Order
  - entity: task
    effect: reads
    facts:
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
    effect: reads
    facts:
    - Name
    - Email
    - Role
    - Participation
  - entity: workspace
    effect: reads
    facts:
    - Name
    - Default access
  - entity: folder
    effect: reads
    facts:
    - Name
    - Workspace
    - Order
    - Expanded
  actor: visitor
  contexts:
    web:
      place: web::public::project
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
---

# Browse project in the demo

## Trigger

The Visitor opens a project, or the Inbox, from the sidebar. The visitor is using the disposable demo.

## Outcome

The project’s tasks are shown section by section, with subtasks under their parents and completed tasks when the Display choice includes them. Projects are grouped by workspace and folder in the sidebar.

## Edge cases

- An empty selection is shown as no matching work; the product does not invent tasks.
