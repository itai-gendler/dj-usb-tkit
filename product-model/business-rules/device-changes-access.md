---
appliesTo:
- type: entity
  id: usb-device
  effect: changes
  facts:
  - Root
  - Name
  - Writable
  - Structure
  - Last seen
  - Listed
  - Database contents
  - Diagnostics
  - Parity
permits:
- actors:
  - dj
references:
- kind: code
  role: implementation
  target: backend/src/service/usb.rs
---

# The DJ changes the drives the app works with

The app has no accounts or roles: whoever uses it on this computer selects, names, initializes, diagnoses and repairs drives. Whether a change completes depends on the drive being present and writable.
