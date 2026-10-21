---
availability:
- place: desktop
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
domain: usb
---

# Remove USB playlist

Remove a device list and content exclusive to it after confirmation.
