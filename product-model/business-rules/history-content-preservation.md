---
appliesTo:
- type: entity
  id: usb-track
- type: capability
  id: remove-usb-playlist
- type: capability
  id: export-playlist
references:
- kind: code
  role: implementation
  target: backend/src/service/usb.rs#remove_usb_playlist_with_progress
- kind: code
  role: implementation
  target: backend/src/service/export.rs
- kind: spec
  role: intent
  target: docs/USB_EXPORT.md
---

# Referenced device content survives playlist cleanup

A recording still used by another USB playlist or play history remains on the drive when another playlist is removed or mirrored.
