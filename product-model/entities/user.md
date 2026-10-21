---
references:
- kind: code
  role: implementation
  target: src/App.tsx
acts: external
kind: person
relations:
- entity: account
  verb: uses
  cardinality: one-to-one
- entity: comment
  verb: authors
  cardinality: one-to-many
---

# User

A person working with their connected Todoist account. Project roles and assignment eligibility are read for each project, rather than being product administration roles.
