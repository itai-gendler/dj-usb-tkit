---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ chooses the explicit PDB menu restore action.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::usb
- text: The Product takes a backup and restores the USB device PDB catalog from eDB, refreshing the category snapshot.
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
  - entity: usb-device
    effect: changes
    facts:
    - Database contents
  actor: dj
  contexts:
    desktop:
      place: desktop::usb
references:
- kind: code
  role: implementation
  target: backend/src/service/repair/player_menu.rs
- kind: code
  role: implementation
  target: vanilla-ui/components/usb/actions.mjs#syncUsbPlayerMenusEdbToPdb
- kind: spec
  role: intent
  target: docs/DIAGNOSTICS_REPAIRS.md
---

# Restore player menu

## Trigger

The DJ chooses the explicit PDB menu restore action.

## Outcome

The Product takes a backup and restores the USB device PDB catalog from eDB, refreshing the category snapshot.
