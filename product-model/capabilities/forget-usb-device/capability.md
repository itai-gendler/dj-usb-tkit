---
availability:
- place: desktop
references:
- kind: code
  role: implementation
  target: backend/src/service/usb.rs#prune_usb_device
- kind: code
  role: implementation
  target: vanilla-ui/components/usb/actions.mjs#pruneUsbDevice
- kind: spec
  role: intent
  target: docs/APP_DATA_MODEL.md
domain: usb
---

# Forget USB device

Remove a remembered root from the recent-device list.
