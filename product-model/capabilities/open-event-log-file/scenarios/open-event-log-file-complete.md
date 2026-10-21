---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ chooses Open log file.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::event-log
- text: The Product opens the session Event Log file through the desktop host.
  kind: product
  entities:
  - entity: event-log
    effect: reads
    facts:
    - Time
    - Level
    - Source
    - Message
    - Count
  actor: dj
  contexts:
    desktop:
      place: desktop::event-log
references:
- kind: code
  role: implementation
  target: vanilla-ui/components/event-log/actions.mjs#openEventLogFile
---

# Open Event Log file

## Trigger

The DJ chooses Open log file.

## Outcome

The Product opens the session Event Log file through the desktop host.
