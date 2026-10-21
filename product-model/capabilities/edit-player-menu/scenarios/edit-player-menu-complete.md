---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ changes visible categories and their order.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::usb
- text: The Product takes a backup and changes USB device category configuration while preserving the full PDB category
    catalog.
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
  target: vanilla-ui/components/usb/actions.mjs
- kind: spec
  role: intent
  target: docs/DIAGNOSTICS_REPAIRS.md
---

# Edit player menu

## Trigger

The DJ changes visible categories and their order.

## Outcome

The Product takes a backup and changes USB device category configuration while preserving the full PDB category catalog.

## Edge cases

- TRACK, PLAYLIST, FOLDER, SEARCH and HISTORY cannot be removed once present.
- The eDB visible-category list is authoritative for the editor; category snapshots follow the save.
