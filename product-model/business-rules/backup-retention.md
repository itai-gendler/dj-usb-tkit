---
appliesTo:
- type: entity
  id: backup
references:
- kind: code
  role: implementation
  target: backend/src/service/usb_backups.rs
- kind: spec
  role: intent
  target: docs/USB_EXPORT.md
---

# A named drive keeps its newest snapshot on the USB and older ones on this computer

Older snapshots move to this computer for a named drive. Retention is per database file across USB and local storage, default ten; oldest local snapshots are pruned first. Unnamed drives keep snapshots on USB. The restore source is protected during its pre-restore retention pass.
