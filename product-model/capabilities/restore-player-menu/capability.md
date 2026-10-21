---
availability:
- place: desktop
references:
- kind: code
  role: implementation
  target: backend/src/service/repair/player_menu.rs
- kind: code
  role: implementation
  target: vanilla-ui/components/usb/actions.mjs#syncUsbPlayerMenusEdbToPdb
- kind: spec
  role: intent
  target: docs/DIAGNOSTICS_REPAIRS.md
domain: usb
---

# Restore player menu

Restore the PDB category catalog from the full eDB catalog when needed.
