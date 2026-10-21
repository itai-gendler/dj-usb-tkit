---
kind: edge
routes:
  desktop: Desktop app
steps:
- text: The DJ requests Export.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::playlist
- text: The Product reports the USB device database conflict.
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
      place: desktop::playlist
references:
- kind: code
  role: implementation
  target: backend/src/service/export.rs#export_to_usb_with_progress
- kind: code
  role: implementation
  target: backend/src/service/export.rs#run_manifest_invariant_check
- kind: code
  role: implementation
  target: vanilla-ui/components/usb/actions.mjs#exportPlaylistToUsb
- kind: spec
  role: intent
  target: docs/USB_EXPORT.md
---

# Report a device write conflict

## Trigger

The database on the drive is changed outside the app after the app read it.

## Outcome

The export does not write over the changed database; selecting the drive again reads it afresh so the export can be retried.
