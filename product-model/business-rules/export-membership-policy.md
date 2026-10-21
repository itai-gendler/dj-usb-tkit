---
appliesTo:
- type: entity
  id: usb-playlist
- type: capability
  id: export-playlist
references:
- kind: code
  role: implementation
  target: backend/src/service/export.rs#export_to_usb_with_progress
- kind: spec
  role: intent
  target: docs/USB_EXPORT.md
---

# Sync mode governs only the target playlist

Mirror replaces target membership/order and prunes unneeded export-owned content; additive preserves existing membership/order and appends missing recordings. Unrelated device lists and player menus remain outside this synchronization.
