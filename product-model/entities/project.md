---
references:
- kind: code
  role: implementation
  target: src/domain/types.ts
relations:
- entity: task
  verb: contains
  cardinality: one-to-many
- entity: section
  verb: contains
  cardinality: one-to-many
- entity: project-member
  verb: has
  cardinality: one-to-many
domain: projects
---

# Project

A named collection of work. The Inbox is the account’s capture project. Visibility and roles describe the external account’s returned information and the controls offered here.

## Information kept

- **Inbox** — Whether this is the account’s fixed capture project.
- **Name** — The project name.
- **Description** — Its description, including the chosen project icon marker.
- **Colour** — The chosen project colour.
- **Favourite** — Whether this project is starred.
- **Workspace** — Its team workspace or personal space.
- **Parent** — An optional containing project or folder.
- **Order** — Its position among sibling projects.
- **Access** — The visibility value reported or requested for this project.
- **My role** — The connected person’s project role as supplied by Todoist.
- **Access editing available** — Whether the current person is reported as project creator or admin.
- **People management available** — Whether the current person is reported as project creator or admin.
- **Assignment allowed** — Whether Todoist has not explicitly disabled assigning tasks in this project.
- **Shared with me** — Whether another active member is the creator and the current person is an active non-creator member.
- **Default view** — The project’s list or board preference.

## States

### Active

A project available for current work.

### Archived

A project put out of the active project list.
