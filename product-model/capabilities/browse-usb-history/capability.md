---
availability:
- place: desktop
references:
- kind: code
  role: implementation
  target: backend/src/service/usb.rs#fetch_usb_histories_with_progress
- kind: code
  role: implementation
  target: backend/src/service/usb.rs#fetch_usb_history_tracks
- kind: spec
  role: intent
  target: docs/USB_IMPORT.md
domain: history
---

# Browse USB history

Read play sessions and their ordered recordings from the selected USB.
