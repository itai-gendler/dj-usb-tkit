---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ chooses Parity Report.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::usb
- text: The Product presents USB device parity for membership, order, metadata, paths, artwork and indexed audio
    presence.
  kind: product
  entities:
  - entity: usb-device
    effect: changes
    facts:
    - Parity
  actor: dj
  contexts:
    desktop:
      place: desktop::usb
references:
- kind: code
  role: implementation
  target: backend/src/service/diagnostics/run.rs#run_usb_parity_report
- kind: spec
  role: intent
  target: docs/DIAGNOSTICS_REPAIRS.md
---

# Compare USB parity

## Trigger

The DJ chooses Parity Report.

## Outcome

The Product presents USB device parity for membership, order, metadata, paths, artwork and indexed audio presence.

## Edge cases

- A usable drive can still have strict parity differences.
- Rating and colour differences are warnings rather than an overall parity failure.
