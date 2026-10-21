---
id: todoist-enhanced
summary: Plan a realistic week, review commitments, and work with Todoist tasks in a front end built around estimates and capacity.
category: productivity
tags:
- task-management
- weekly-planning
- todoist
authors:
- name: Jules-Valentin Bertolino
  url: https://github.com/julesvbertolino
license: MIT
languages:
- en
- fr
limitations:
- People connect an existing Todoist account; this product has no separate account service.
- Todoist remains the external system for account permissions, saved work and authoritative recurrence results; this product submits requests and handles its responses.
- Demo work is disposable and is never sent to Todoist.
- Gathering dust acknowledgements and transient planning selections belong to the device or current session.
- Recurring forecasts are read-only estimates of supported rules, not additional saved tasks.
references:
- kind: doc
  role: intent
  target: README.md
- kind: code
  role: implementation
  target: src/app-info.ts
- kind: code
  role: implementation
  target: src/store/sync.ts
- kind: code
  role: implementation
  target: src/domain/projectOccurrences.ts
- kind: doc
  role: context
  target: LICENSE
---

# Enhanced for Todoist

An independent front end for Todoist that helps a person decide what belongs today, anytime this week, or Someday. It combines task estimates with available hours, guided reviews, shared projects, calendar planning, and a record of completed work. The same browser product serves large and small screens and can be installed where the browser supports it.

## Intent

“Todoist just got even more powerful, with a new front end to display your tasks. The data stays in Todoist, but now you can plan a week, have a review, and get a lot of new features and visual enhancements.” Todoist asks which day a task belongs to, “and most work has no good answer — it belongs to *this week*”, so there are three commitments instead of one: Today, Anytime this week and Someday. Estimates are measured against the hours available, so that “a day filled to 140% says so before you start it, not at six in the evening”, and daily and weekly reviews take “a few minutes, one question at a time, with an end”. Everything is stored in properties Todoist already has, so “if this project stopped working tomorrow your data would be untouched”. Enhanced for Todoist is an independent project, not created by, affiliated with, or supported by Todoist.
