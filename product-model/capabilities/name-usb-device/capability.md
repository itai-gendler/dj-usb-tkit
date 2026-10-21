---
availability:
- place: desktop
references:
- kind: code
  role: implementation
  target: backend/src/service/usb.rs#set_usb_device_name
- kind: code
  role: implementation
  target: backend/src/service/usb_identity.rs#validate_name
- kind: spec
  role: intent
  target: docs/USB_EXPORT.md
domain: usb
---

# Name USB device

Set or change the portable drive name used to recognize it across connections.
