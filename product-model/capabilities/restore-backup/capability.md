---
availability:
- place: desktop
references:
- kind: code
  role: implementation
  target: backend/src/service/usb_backups.rs#restore_usb_backup
- kind: code
  role: implementation
  target: vanilla-ui/components/backups/actions.mjs
- kind: spec
  role: intent
  target: docs/USB_EXPORT.md
domain: backups
---

# Restore backup

Put a database snapshot back onto the selected drive.
