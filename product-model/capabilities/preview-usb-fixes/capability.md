---
availability:
- place: desktop
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
domain: usb
---

# Preview USB fixes

Inspect proposed repairs and their effects before choosing an apply operation.
