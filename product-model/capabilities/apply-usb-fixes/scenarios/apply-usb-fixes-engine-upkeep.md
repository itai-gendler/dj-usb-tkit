---
kind: alternate
routes:
  desktop: Desktop app
steps:
- text: The DJ selects the optional Engine DJ upkeep proposal and applies it.
  kind: actor
  actor: dj
  entities: []
  contexts:
    desktop:
      place: desktop::usb
- text: The Product saves settings with Write Engine DJ library enabled.
  kind: product
  actor: dj
  entities:
  - entity: settings
    effect: changes
    facts:
    - Write Engine DJ library
  contexts:
    desktop:
      place: desktop::usb
- text: The Product rebuilds USB device Engine DJ output and reports the repair fix result.
  kind: product
  actor: dj
  entities:
  - entity: usb-device
    effect: changes
    facts:
    - Engine DJ library
  - entity: repair-fix
    effect: changes
    from: Proposed
    to: Applied
    facts:
    - Result
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
- kind: code
  role: implementation
  target: backend/src/service/engine_export.rs#enable_engine_library
---

# Enable upkeep for an existing Engine DJ library

## Trigger

A drive already has an Engine DJ library whose upkeep is disabled or whose contents are behind the PDB.

## Outcome

The optional repair enables the preference and rebuilds the player library. The desktop preference display follows the saved value.

## Edge cases

- This proposal is optional and is not part of the default selected set.
- A rebuilding error appears as a failed repair result.
