---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ opens the snapshot list for the selected drive.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::backups
- text: The Product presents backup snapshots from the USB and this computer, grouping PDB/eDB files by timestamp.
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
  actor: dj
  contexts:
    desktop:
      place: desktop::backups
references:
- kind: code
  role: implementation
  target: backend/src/service/usb_backups.rs#list_usb_backups
- kind: code
  role: implementation
  target: vanilla-ui/components/backups/actions.mjs
- kind: spec
  role: intent
  target: docs/USB_EXPORT.md
---

# Browse backups

## Trigger

The DJ opens Backups for the selected drive.

## Outcome

The Product presents backup snapshots from the USB and this computer, grouping PDB/eDB files by timestamp.

## Edge cases

- The snapshot includes whichever database files existed at that timestamp.
