---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ chooses the repair selections and Apply Fixes.
  kind: actor
  entities:
  - entity: repair-fix
    effect: changes
    facts:
    - Selection
  actor: dj
  contexts:
    desktop:
      place: desktop::usb
- text: The Product creates a backup and applies the selected repair fix to USB device database contents.
  kind: product
  entities:
  - entity: backup
    effect: creates
    facts:
    - Timestamp
    - Files
    - Location
    - Reason
    - Playlist count
  - entity: repair-fix
    effect: changes
    from: Proposed
    to: Applied
    facts:
    - Result
  - entity: usb-device
    effect: changes
    facts:
    - Database contents
    - Diagnostics
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

# Apply selected repairs

## Trigger

The DJ has reviewed current proposals.

## Outcome

Applied fixes and refreshed diagnostics are shown; successful changes clear stale device list views.

## Edge cases

- At least one proposal must be selected in the desktop flow.
- Accompanying bookkeeping is included in an apply.
- Strict parity repair preserves membership from both database sides, prefers available eDB metadata and does not compact the PDB.
