---
appliesTo:
- type: entity
  id: backup
- type: capability
  id: export-playlist
- type: capability
  id: reorder-usb-playlists
- type: capability
  id: remove-usb-playlist
- type: capability
  id: apply-usb-fixes
- type: capability
  id: edit-player-menu
- type: capability
  id: restore-player-menu
- type: capability
  id: restore-backup
references:
- kind: code
  role: implementation
  target: backend/src/service/usb_backups.rs
- kind: code
  role: implementation
  target: backend/src/service/usb_vendor_compat.rs
- kind: spec
  role: intent
  target: docs/USB_EXPORT.md
---

# Exports, USB playlist changes, repairs, menu changes and restores snapshot the databases first

Export takes a snapshot of the existing PDB and eDB unless Backup before export is off. Reordering or removing USB playlists, applying repairs, changing the player menu and restoring a backup always take one first. A snapshot groups the files that existed under one timestamp and holds no audio.
