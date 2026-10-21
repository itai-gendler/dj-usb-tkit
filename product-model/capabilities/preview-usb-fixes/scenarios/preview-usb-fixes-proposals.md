---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ chooses Preview Fixes.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::usb
- text: The Product reads USB device findings and creates repair fix proposals.
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
  - entity: repair-fix
    effect: creates
    to: Proposed
    facts:
    - Title
    - Description
    - Supported
    - Destructive
    - Estimated changes
    - Selection
    - Result
  actor: dj
  contexts:
    desktop:
      place: desktop::usb
references:
- kind: code
  role: implementation
  target: backend/src/service/repair/run.rs
- kind: code
  role: implementation
  target: vanilla-ui/components/usb/actions.mjs#previewUsbRepairs
- kind: spec
  role: intent
  target: docs/DIAGNOSTICS_REPAIRS.md
---

# Preview repair choices

## Trigger

The selected drive has diagnostic findings.

## Outcome

Supported proposals and manual cases are shown with estimated writes/deletes and destructive flags; preview does not apply repairs.

## Edge cases

- History synchronization and Engine DJ upkeep are optional selections.
- Required structural proposals stay selected in the desktop preview.
- Unrecoverable media cases describe a manual recovery need.
