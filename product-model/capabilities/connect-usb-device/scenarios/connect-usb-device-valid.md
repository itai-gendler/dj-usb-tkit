---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ selects the drive folder.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::usb
- text: The Product records the USB device root, structure and last seen information.
  kind: product
  entities:
  - entity: usb-device
    effect: creates
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
    - Listed
  actor: dj
  contexts:
    desktop:
      place: desktop::usb
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
---

# Connect an existing export

## Trigger

The DJ selects a drive folder.

## Outcome

The app remembers the root, reports structure and writability, and requests a name for an unnamed valid drive.

## Edge cases

- A missing or empty path reports validation warnings.
- A read-only root can still be used for imports.
- Changing the selected root waits for the active USB operation to finish.
