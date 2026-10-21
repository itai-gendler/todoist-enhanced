---
references:
- kind: code
  role: implementation
  target: src/store/prefs.ts
---

# Settings

Choices belonging to the current person. Account settings are synchronized through an Inbox comment; the demo can illustrate them.

## Information kept

- **Language** — English or French.
- **General** — Homepage, date and time formats, natural date recognition, section search and completion feedback preferences.
- **Appearance** — The chosen appearance preferences, including light, dark or system mode and accent.
- **Sidebar** — The selected entries, counts and workspace ordering.
- **Lists** — The chosen task information and opening preferences.
- **Week label** — The case-insensitive label denoting undated weekly commitments; week by default.
- **Quick group** — Whether quick work is grouped separately.
- **Dust group** — Whether old Someday work is surfaced.
- **Dust delay** — One, two, three, six or twelve calendar months; three by default.
- **Quiet delay** — The positive number of days selected for project review.
- **Daily capacity** — Available minutes for each weekday; five hours each by default.
- **Weekly override** — A positive explicit weekly total, or no override so daily capacities are summed.
- **Estimate storage** — Tags by default or native duration after selection.
- **Conflict checks** — Which supported contradiction checks are shown.
- **Matrix rules** — Selected urgency buckets, important priorities, and inclusion of future and Someday work.
- **Dashboard arrangement** — The selected dashboard card order and display choices.
- **Setup completion** — Whether first-run choices have been acknowledged.
- **Release notices** — Whether to show new releases and which release was last acknowledged.
