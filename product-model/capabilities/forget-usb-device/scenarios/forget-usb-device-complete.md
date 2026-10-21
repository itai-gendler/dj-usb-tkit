---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ removes a remembered root.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::usb
- text: The Product hides the USB device from the recent list while keeping its underlying identity records and
    the physical drive contents.
  kind: product
  entities:
  - entity: usb-device
    effect: changes
    facts:
    - Listed
  actor: dj
  contexts:
    desktop:
      place: desktop::usb
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
---

# Forget USB device

## Trigger

The DJ removes a remembered root.

## Outcome

The Product hides the USB device from the recent list while keeping its underlying identity records and the physical drive contents.
