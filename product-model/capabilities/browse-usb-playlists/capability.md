---
availability:
- place: desktop
references:
- kind: code
  role: implementation
  target: backend/src/service/usb.rs#fetch_usb_playlists_with_progress
- kind: code
  role: implementation
  target: backend/src/service/usb.rs#fetch_usb_playlist_tracks
- kind: spec
  role: intent
  target: docs/USB_IMPORT.md
domain: usb
---

# Browse USB playlists

Read the playlists on the selected drive and load the recordings of the one chosen.
