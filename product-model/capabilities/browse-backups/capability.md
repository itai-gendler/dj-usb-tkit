---
availability:
- place: desktop
references:
- kind: code
  role: implementation
  target: backend/src/service/usb_backups.rs#list_usb_backups
- kind: code
  role: implementation
  target: vanilla-ui/components/backups/actions.mjs
- kind: spec
  role: intent
  target: docs/USB_EXPORT.md
domain: backups
---

# Browse backups

List the database snapshots of the selected drive, kept on the drive and on this computer.
