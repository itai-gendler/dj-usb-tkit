---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ chooses a snapshot and confirms Restore.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::backups
- text: The Product creates a backup of existing live databases, protecting the selected restore source during retention.
  kind: product
  actor: dj
  entities:
  - entity: backup
    effect: creates
    facts:
    - Timestamp
    - Files
    - Location
    - Reason
    - Playlist count
    as: current-state
  contexts:
    desktop:
      place: desktop::backups
- text: The Product restores the backup database files onto the USB device and reloads what the drive shows.
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
    as: restore-source
  - entity: usb-device
    effect: changes
    facts:
    - Database contents
    - Diagnostics
    - Parity
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

# Restore backup

## Trigger

The DJ chooses a snapshot and confirms Restore.

## Outcome

The drive has the chosen snapshot's databases again, and the USB Browser shows its restored playlists.

## Edge cases

- A missing snapshot is reported; cancelling confirmation leaves it unchanged.
