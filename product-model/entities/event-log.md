---
references:
- kind: code
  role: implementation
  target: vanilla-ui/components/event-log/actions.mjs
- kind: code
  role: implementation
  target: vanilla-ui/event_log.mjs
---

# Event Log

The user-visible record of job messages, warnings and operation outcomes.

## Information kept

- **Time** — Occurrence time.
- **Level** — Severity.
- **Source** — Reporting area.
- **Message** — Message and details.
- **Count** — Coalesced repetition count.
