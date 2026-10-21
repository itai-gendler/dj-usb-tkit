---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ opens the operation messages and chooses severity/source filters.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::event-log
- text: The Product presents Event Log messages, details and repeated occurrence counts.
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
  target: vanilla-ui/components/event-log/actions.mjs
---

# Browse Event Log

## Trigger

The DJ opens the operation messages and chooses severity/source filters.

## Outcome

The Product presents Event Log messages, details and repeated occurrence counts.
