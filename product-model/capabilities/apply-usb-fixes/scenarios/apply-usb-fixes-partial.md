---
kind: edge
routes:
  desktop: Desktop app
steps:
- text: The DJ applies the reviewed selection.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::usb
- text: The Product reports a failed repair fix and continues reporting the remaining actions.
  kind: product
  entities:
  - entity: repair-fix
    effect: changes
    from: Proposed
    to: Failed
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

# Report mixed repair results

## Trigger

Some selected actions fail or no longer apply.

## Outcome

The report separates applied, skipped and failed actions, retaining the results of successful work.
