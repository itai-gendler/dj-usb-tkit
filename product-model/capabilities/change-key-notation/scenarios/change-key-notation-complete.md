---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ chooses Classic or Camelot key notation.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::key-notation
- text: The Product saves the key notation in settings and shows keys in it.
  kind: product
  entities:
  - entity: settings
    effect: changes
    facts:
    - Key notation
  actor: dj
  contexts:
    desktop:
      place: desktop::key-notation
references:
- kind: code
  role: implementation
  target: vanilla-ui/components/settings/events.mjs
- kind: code
  role: implementation
  target: backend/src/service/settings.rs#set_frontend_setting
- kind: spec
  role: intent
  target: docs/APP_DATA_MODEL.md
---

# Change key notation

## Trigger

The DJ chooses the desired preference values.

## Outcome

Keys everywhere in the app are shown in the chosen notation; stored keys do not change.
