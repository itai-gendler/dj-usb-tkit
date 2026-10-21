---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ confirms removing a device list.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::usb
- text: The Product takes a backup, removes the USB playlist and its exclusive USB tracks, and retains recordings
    referenced by other lists or device history.
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
  - entity: usb-playlist
    effect: removes
  - entity: usb-track
    effect: removes
  actor: dj
  contexts:
    desktop:
      place: desktop::usb
references:
- kind: code
  role: implementation
  target: backend/src/service/usb.rs#remove_usb_playlist_with_progress
- kind: code
  role: implementation
  target: vanilla-ui/components/usb/actions.mjs
- kind: spec
  role: intent
  target: docs/USB_EXPORT.md
---

# Remove USB playlist

## Trigger

The DJ confirms removing a device list.

## Outcome

The Product takes a backup, removes the USB playlist and its exclusive USB tracks, and retains recordings referenced by other lists or device history.
