---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ chooses the sync mode and whether to write an Engine DJ library.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::export-settings
- text: The Product saves the export choices in settings and rechecks which lists have their order locked.
  kind: product
  entities:
  - entity: settings
    effect: changes
    facts:
    - Sync mode
    - Write Engine DJ library
  actor: dj
  contexts:
    desktop:
      place: desktop::export-settings
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

# Change Export settings

## Trigger

The DJ chooses the desired preference values.

## Outcome

Later exports use the chosen sync mode, and with Write Engine DJ library on, later changes to a drive rebuild its Engine DJ library.
