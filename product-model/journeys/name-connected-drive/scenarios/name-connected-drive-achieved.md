---
kind: primary
result: achieved
routes:
  desktop: Desktop app
steps:
- text: The DJ selects an unnamed valid drive.
  kind: actor
  actor: dj
  entities: []
  capability: connect-usb-device
  contexts:
    desktop:
      place: desktop::usb
- text: The Product records the USB device and opens its naming prompt.
  kind: product
  actor: dj
  entities:
  - entity: usb-device
    effect: creates
    facts:
    - Root
    - Name
    - Writable
    - Structure
    - Last seen
    - Listed
    - Database contents
    - Engine DJ library
    - Diagnostics
    - Parity
  capability: connect-usb-device
  contexts:
    desktop:
      place: desktop::usb
- text: The DJ supplies the portable name.
  kind: actor
  actor: dj
  entities: []
  capability: name-usb-device
  contexts:
    desktop:
      place: desktop::usb
- text: The Product saves the USB device name.
  kind: product
  actor: dj
  entities:
  - entity: usb-device
    effect: changes
    facts:
    - Name
  capability: name-usb-device
  contexts:
    desktop:
      place: desktop::usb
references:
- kind: code
  role: implementation
  target: vanilla-ui/components/usb/actions.mjs#validateAndSetUsbRoot
- kind: code
  role: implementation
  target: vanilla-ui/components/usb/actions.mjs#promptDriveNameIfUnset
---

# Name the connected drive

## Trigger

The DJ connects a valid drive that has no name.

## Outcome

The app prompts for and saves the portable name.
