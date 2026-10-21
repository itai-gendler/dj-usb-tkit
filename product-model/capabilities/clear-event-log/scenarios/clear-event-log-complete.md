---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ chooses Clear.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::event-log
- text: The Product clears the displayed Event Log and unseen error count; the session log file remains.
  kind: product
  entities:
  - entity: event-log
    effect: changes
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
  target: vanilla-ui/components/event-log/events.mjs
---

# Clear Event Log

## Trigger

The DJ chooses Clear.

## Outcome

The Product clears the displayed Event Log and unseen error count; the session log file remains.
