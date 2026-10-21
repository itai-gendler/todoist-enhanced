---
appliesTo:
- type: entity
  id: tag
  effect: changes
  facts:
  - Name
references:
- kind: code
  role: implementation
  target: src/domain/renameLabel.ts
permits:
- actors:
  - user
  - visitor
  when:
  - fact: Reserved
    is: false
---

# Users rename only nonreserved tags

The configured week label, week, quick, automation, waiting and names starting est- are reserved for renaming. A new name must also be nonempty, nonreserved and unique ignoring case.
