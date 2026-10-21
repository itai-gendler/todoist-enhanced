---
appliesTo:
- type: entity
  id: task
  effect: changes
  facts:
  - Native duration
  contexts:
  - place: web::connected::task
  - place: web::connected::review
  - place: web::connected::issues
references:
- kind: code
  role: implementation
  target: src/domain/estimates.ts
- kind: code
  role: implementation
  target: src/store/tasks.ts
- kind: code
  role: implementation
  target: src/store/estimate-safety.ts
permits:
- actors:
  - user
  when:
  - entity: account
    fact: Duration storage allowed
    is: true
- unattended: true
  when:
  - entity: account
    fact: Duration storage allowed
    is: true
---

# Users request native estimates only when their account is eligible

An explicitly free account is routed to tag estimates unless the reported premium or team status permits native duration. Unknown plans may be tried and every native estimate request is checked against server data.
