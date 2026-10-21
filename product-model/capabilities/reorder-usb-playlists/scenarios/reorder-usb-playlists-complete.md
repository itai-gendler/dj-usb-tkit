---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ chooses a new device list order.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::usb
- text: The Product saves USB playlist menu order after taking a backup of existing databases.
  kind: product
  entities:
  - entity: usb-playlist
    effect: changes
    facts:
    - Menu order
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
      place: desktop::usb
references:
- kind: code
  role: implementation
  target: backend/src/service/usb.rs#reorder_usb_playlists_with_progress
- kind: code
  role: implementation
  target: vanilla-ui/components/usb/actions.mjs#reorderUsbPlaylists
- kind: spec
  role: intent
  target: docs/USB_EXPORT.md
---

# Reorder USB playlists

## Trigger

The DJ chooses a new device list order.

## Outcome

The Product saves USB playlist menu order after taking a backup of existing databases.

## Edge cases

- A request with no PDB-backed list identities is rejected.
