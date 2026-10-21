---
availability:
- place: desktop
references:
- kind: code
  role: implementation
  target: backend/src/service/usb_utils.rs#initialize_usb
- kind: code
  role: implementation
  target: vanilla-ui/components/usb/actions.mjs#initializeUsb
- kind: spec
  role: intent
  target: docs/USB_EXPORT.md
domain: usb
---

# Initialize USB device

Create missing player database structure in an existing writable directory.
