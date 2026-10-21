---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ opens the remembered device list.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::usb
- text: The Product presents USB device names and roots in most-recently-seen order.
  kind: product
  entities:
  - entity: usb-device
    effect: reads
    facts:
    - Root
    - Name
    - Writable
    - Structure
    - Last seen
    - Database contents
    - Engine DJ library
    - Diagnostics
    - Parity
  actor: dj
  contexts:
    desktop:
      place: desktop::usb
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
---

# Browse USB devices

## Trigger

The DJ opens the remembered device list.

## Outcome

The Product presents USB device names and roots in most-recently-seen order.
