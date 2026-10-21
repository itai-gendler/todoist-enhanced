---
appliesTo:
- type: capability
  id: browse-insights
- type: capability
  id: run-review
references:
- kind: code
  role: implementation
  target: src/domain/insights.ts#focusScore
---

# Focus score weights completed tasks by priority

P1, P2, P3 and P4 contribute weights four, three, two and one. The score is the weighted total divided by four times the number of completed tasks, as a rounded percentage: 100 when everything finished was P1, 25 when everything was P4. No completions yields zero. Missing priorities count as P4. It is a priority-weighted count, not a measure of tracked effort.
