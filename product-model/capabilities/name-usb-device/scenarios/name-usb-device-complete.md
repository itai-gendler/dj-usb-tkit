---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ supplies a drive name.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::usb
- text: The Product writes the USB device name to its portable marker and local remembered identity.
  kind: product
  entities:
  - entity: usb-device
    effect: changes
    facts:
    - Name
  actor: dj
  contexts:
    desktop:
      place: desktop::usb
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
---

# Name USB device

## Trigger

The DJ supplies a drive name.

## Outcome

The Product writes the USB device name to its portable marker and local remembered identity.

## Edge cases

- The trimmed name must be non-empty and at most 80 characters.
- A name already assigned to another known drive is rejected.
- A detected filesystem volume label can be suggested without being accepted automatically.

- Choosing Not now on the initial prompt leaves the drive unnamed and usable.
