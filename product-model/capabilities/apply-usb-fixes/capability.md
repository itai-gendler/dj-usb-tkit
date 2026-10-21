---
availability:
- place: desktop
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
domain: usb
---

# Apply USB fixes

Apply the checked supported proposals, with database backup and per-fix outcomes.
