---
scope: Core browser planning, task and project work, account connection, collaboration, review and completion history.
method: Static source tracing and selective test/document reading at the pinned upstream commit; no application execution.
covered:
- description: Browser entry, routing, connection and first-run processes.
  paths:
  - src/App.tsx
  - src/views/ConnectView.tsx
  - src/api/auth.ts
  - src/api/oauth.ts
  - src/hooks/useRoute.ts
  - src/components/overlays/Walkthrough.tsx
  - src/components/overlays/Tour.tsx
- description: Weekly, upcoming, Someday, review, matrix and time-fitting views with their domain rules.
  paths:
  - src/views/WeekView.tsx
  - src/views/UpcomingView.tsx
  - src/views/SimpleListView.tsx
  - src/views/ReviewView.tsx
  - src/views/EisenhowerView.tsx
  - src/domain/views.ts
  - src/domain/load.ts
  - src/domain/review.ts
  - src/domain/fits.ts
  - src/domain/eisenhower.ts
  - src/components/TimePanel.tsx
- description: Task authoring, hierarchy, description checklists, estimates and calendar operations.
  paths:
  - src/store/tasks.ts
  - src/store/tasks-move.ts
  - src/store/calendar.ts
  - src/store/estimate-safety.ts
  - src/domain/estimates.ts
  - src/domain/estimate-conversion.ts
  - src/domain/dnd.ts
  - src/domain/checklist.ts
  - src/domain/projectOccurrences.ts
  - src/components/overlays/Composer.tsx
  - src/components/overlays/TaskDetail.tsx
  - src/components/overlays/EstimateConversion.tsx
  - src/components/CalendarSurface.tsx
  - src/components/BulkBar.tsx
- description: Project and section structure, tags, saved filters, sharing and task discussion.
  paths:
  - src/store/structure.ts
  - src/store/collab.ts
  - src/views/ProjectView.tsx
  - src/views/LabelsView.tsx
  - src/views/FiltersView.tsx
  - src/domain/sharing.ts
  - src/domain/projectAccess.ts
  - src/domain/assignees.ts
  - src/components/CommentThread.tsx
  - src/components/overlays/ShareSheet.tsx
  - src/api/filters.ts
  - src/hooks/useFilterResult.ts
- description: Settings, device persistence, synchronization and scoped display selection.
  paths:
  - src/views/SettingsView.tsx
  - src/store/prefs.ts
  - src/store/preferences.ts
  - src/store/sync.ts
  - src/store/dust.ts
  - src/db/idb.ts
  - src/hooks/useData.ts
  - src/store/selectors.ts
- description: Insights, Logbook, history retrieval, search, conflicts and notification reading.
  paths:
  - src/views/InsightsView.tsx
  - src/views/SearchView.tsx
  - src/domain/insights.ts
  - src/domain/periods.ts
  - src/domain/logbook.ts
  - src/api/completed.ts
  - src/hooks/useCompleted.ts
  - src/domain/search.ts
  - src/domain/conflicts.ts
  - src/domain/notifications.ts
  - src/components/overlays/Issues.tsx
exclusions:
- description: Build tooling, release packaging and CI are development processes rather than product abilities.
  paths:
  - scripts/
  - .github/workflows/
  - vite.config.ts
  - package.json
- description: Visual styling, icon catalogues, illustrative media and mockups are presentation design.
  paths:
  - src/styles/
  - public/
  - docs/mockups/
  - src/components/charts.tsx
  - src/domain/projectIconCatalog.ts
- description: Test harnesses and fixtures supply inspection leads, not independently supported interfaces.
  paths:
  - e2e/
  - src/test/
  - playwright.config.ts
  - vitest.config.ts
unmapped:
- description: Native wrapper quick-add window.
  paths:
  - src/QuickAdd.tsx
  - src/domain/macApp.ts
  - src/components/MacApp.tsx
- description: Browser installation prompt.
  paths:
  - src/lib/install.ts
  - src/components/overlays/InstallPrompt.tsx
- description: What's new, feedback, hiring and support notes.
  paths:
  - src/components/overlays/WhatsNew.tsx
  - src/components/overlays/Feedback.tsx
  - src/components/HireNote.tsx
  - src/components/CoffeeLine.tsx
  - .github/ISSUE_TEMPLATE/config.yml
- description: Copy-link actions, shortcut help and keyboard navigation.
  paths:
  - src/api/links.ts
  - src/components/overlays/Shortcuts.tsx
  - src/hooks/useKeyboard.ts
- description: Habit and streak panel, and the reminder details of the task panel.
  paths:
  - src/components/overlays/InsightsPanel.tsx
  - src/domain/nextOccurrence.ts
  - src/components/overlays/TaskDetail.tsx
- description: The route from a first sign-in into Setup.
  paths:
  - src/App.tsx
  - src/views/ConnectView.tsx
- description: Quiet-project detection in the weekly review.
  paths:
  - src/domain/review.ts
- description: Project duplication details beyond the copied project, sections and open tasks.
  paths:
  - src/store/structure.ts
limitations: []
---

# Coverage


