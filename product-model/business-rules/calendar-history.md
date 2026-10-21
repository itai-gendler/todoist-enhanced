---
appliesTo:
- type: capability
  id: browse-filter-results
- type: capability
  id: browse-project
- type: capability
  id: browse-upcoming
references:
- kind: code
  role: implementation
  target: src/hooks/useCalendarHistory.ts#useCalendarHistory
- kind: code
  role: implementation
  target: src/components/CalendarSurface.tsx
---

# Calendar history belongs to completion day

Fetched completed-history entries are shown on their completion day, not an assumed former scheduled date. Saved-filter calendars retain locally completed matches because the query endpoint supplies open matches; this does not reconstruct all historical query matches.
