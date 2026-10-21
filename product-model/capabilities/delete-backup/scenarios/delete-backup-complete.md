---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ chooses a snapshot and confirms Delete.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::backups
- text: The Product deletes the backup files belonging to that timestamp and refreshes the list.
  kind: product
  entities:
  - entity: backup
    effect: removes
  actor: dj
  contexts:
    desktop:
      place: desktop::backups
references:
- kind: code
  role: implementation
  target: backend/src/service/usb_backups.rs#delete_usb_backup
- kind: code
  role: implementation
  target: vanilla-ui/components/backups/actions.mjs
- kind: spec
  role: intent
  target: docs/USB_EXPORT.md
---

# Delete backup

## Trigger

The DJ chooses a snapshot and confirms Delete.

## Outcome

The Product deletes the backup files belonging to that timestamp and refreshes the list.

## Edge cases

- A missing snapshot is reported; cancelling confirmation leaves it unchanged.
