---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ chooses Initialize for the selected directory.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::usb
- text: The Product creates missing USB device folders and baseline PDB/eDB files, then revalidates the root.
  kind: product
  entities:
  - entity: usb-device
    effect: changes
    facts:
    - Structure
    - Database contents
  actor: dj
  contexts:
    desktop:
      place: desktop::usb
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
---

# Initialize USB device

## Trigger

The DJ chooses Initialize for the selected directory.

## Outcome

The Product creates missing USB device folders and baseline PDB/eDB files, then revalidates the root.

## Edge cases

- Existing database files are retained.
- Partitioning and filesystem formatting are performed outside the app.
