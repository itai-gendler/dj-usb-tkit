---
entities:
- entity: usb-device
  shows:
  - Name
  - Root
- entity: backup
  shows:
  - Timestamp
  - Files
  - Location
  - Reason
  - Playlist count
references:
- kind: code
  role: implementation
  target: vanilla-ui/index.html
---

# Backups

Inspect database snapshots for the selected drive and choose a restore point.
