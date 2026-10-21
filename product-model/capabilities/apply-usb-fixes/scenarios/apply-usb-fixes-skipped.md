---
kind: alternate
routes:
  desktop: Desktop app
steps:
- text: The DJ applies other selected actions.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::usb
- text: The Product records the repair fix as skipped.
  kind: product
  entities:
  - entity: repair-fix
    effect: changes
    from: Proposed
    to: Skipped
    facts:
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
  target: vanilla-ui/components/usb/actions.mjs#applyUsbRepairs
- kind: spec
  role: intent
  target: docs/DIAGNOSTICS_REPAIRS.md
---

# Report a skipped proposal

## Trigger

A proposal is not selected or has nothing left to repair.

## Outcome

The proposal is reported as skipped.
