---
availability:
- place: desktop
references:
- kind: code
  role: implementation
  target: backend/src/service/usb_backups.rs#delete_usb_backup
- kind: code
  role: implementation
  target: vanilla-ui/components/backups/actions.mjs
- kind: spec
  role: intent
  target: docs/USB_EXPORT.md
domain: backups
---

# Delete backup

Delete one database snapshot of the selected drive.
