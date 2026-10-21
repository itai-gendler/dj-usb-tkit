---
kind: alternate
routes:
  desktop: Desktop app
steps:
- text: The DJ selects the directory.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::usb
- text: The Product presents USB device structure and write availability.
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
  target: backend/src/service/usb.rs#validate_usb_root
- kind: code
  role: implementation
  target: vanilla-ui/components/usb/actions.mjs#validateAndSetUsbRoot
- kind: spec
  role: intent
  target: docs/USB_EXPORT.md
---

# Find a drive needing initialization

## Trigger

The chosen directory lacks the expected export folders or databases.

## Outcome

The app reports the missing structure and offers initialization for a writable root.
