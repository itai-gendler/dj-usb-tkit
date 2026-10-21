---
kind: alternate
routes:
  desktop: Desktop app
steps:
- text: The DJ confirms restoring the old snapshot.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::backups
- text: The Product creates a backup of the live databases while protecting the selected timestamp.
  kind: product
  entities:
  - entity: backup
    effect: creates
    facts:
    - Timestamp
    - Files
    - Location
    - Reason
    - Playlist count
  actor: dj
  contexts:
    desktop:
      place: desktop::backups
- text: The Product resolves the protected backup at its current location and restores USB device database contents.
  kind: product
  entities:
  - entity: backup
    effect: reads
    facts:
    - Timestamp
    - Files
    - Location
    - Reason
    - Playlist count
  - entity: usb-device
    effect: changes
    facts:
    - Database contents
  actor: dj
  contexts:
    desktop:
      place: desktop::backups
references:
- kind: code
  role: implementation
  target: backend/src/service/usb_backups.rs#restore_usb_backup
- kind: code
  role: implementation
  target: vanilla-ui/components/backups/actions.mjs
- kind: spec
  role: intent
  target: docs/USB_EXPORT.md
---

# Restore an old snapshot with retention set to one

## Trigger

The selected snapshot is old and retention is one.

## Outcome

The live databases are backed up first; the chosen restore source survives that retention pass even if it is moved to local storage.
