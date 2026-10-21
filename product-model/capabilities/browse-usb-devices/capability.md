---
availability:
- place: desktop
references:
- kind: code
  role: implementation
  target: backend/src/service/usb.rs#list_usb_devices
- kind: code
  role: implementation
  target: vanilla-ui/components/usb/actions.mjs#loadUsbDevices
- kind: spec
  role: intent
  target: docs/APP_DATA_MODEL.md
domain: usb
---

# Browse USB devices

Inspect remembered roots and their latest connection information.
