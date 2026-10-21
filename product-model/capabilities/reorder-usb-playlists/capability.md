---
availability:
- place: desktop
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
domain: usb
---

# Reorder USB playlists

Save device playlist menu order in PDB and eDB.
