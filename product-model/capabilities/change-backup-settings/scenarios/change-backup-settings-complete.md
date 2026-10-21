---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ chooses whether to snapshot the databases before export and how many snapshots to keep per file.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::backup-settings
- text: The Product saves these choices in settings.
  kind: product
  entities:
  - entity: settings
    effect: changes
    facts:
    - Backup before export
    - Backup retention
  actor: dj
  contexts:
    desktop:
      place: desktop::backup-settings
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

# Change Backups settings

## Trigger

The DJ chooses the desired preference values.

## Outcome

The next export follows the backup choice, and the next backup keeps the chosen number of snapshots per database file.
