---
appliesTo:
- type: entity
  id: usb-device
- type: capability
  id: diagnose-usb-device
- type: capability
  id: compare-usb-parity
- type: capability
  id: preview-usb-fixes
references:
- kind: code
  role: implementation
  target: backend/src/service/diagnostics/run.rs
- kind: spec
  role: intent
  target: docs/DIAGNOSTICS_REPAIRS.md
---

# Operational diagnostics and strict parity are distinct reports

Operational passability does not imply field-for-field agreement between PDB and eDB. Reporting and preview do not apply repairs; changes require an explicit apply operation.
