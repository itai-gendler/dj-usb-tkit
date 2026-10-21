---
availability:
- place: desktop
references:
- kind: code
  role: implementation
  target: backend/src/service/usb.rs#validate_usb_root
- kind: code
  role: implementation
  target: vanilla-ui/components/usb/actions.mjs#validateAndSetUsbRoot
- kind: spec
  role: intent
  target: docs/USB_EXPORT.md
domain: usb
---

# Connect USB device

Select a USB folder or a remembered device and inspect its available structure.
