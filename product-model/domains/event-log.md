---
references:
- kind: code
  role: implementation
  target: vanilla-ui/components/event-log/actions.mjs
---

# Event Log

The Event Log: the messages, warnings and outcomes that app operations report.

## Boundary

Owns reading and clearing the displayed log and opening the session log file. Does not own the diagnostics or repair decisions those messages describe.
