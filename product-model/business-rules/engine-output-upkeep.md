---
appliesTo:
- type: entity
  id: usb-device
- type: capability
  id: export-playlist
- type: capability
  id: reorder-usb-playlists
- type: capability
  id: remove-usb-playlist
- type: capability
  id: restore-backup
- type: capability
  id: apply-usb-fixes
- type: capability
  id: edit-player-menu
- type: capability
  id: restore-player-menu
- type: capability
  id: edit-cue
- type: capability
  id: edit-beat-grid
- type: capability
  id: edit-track-metadata
references:
- kind: code
  role: implementation
  target: backend/src/service/engine_export.rs#refresh_engine_library
- kind: spec
  role: intent
  target: docs/ENGINE_DJ.md
---

# An enabled Engine DJ library follows every change to the drive

With Write Engine DJ library enabled, USB mutations rebuild the Engine DJ projection from the device's PDB and analysis bundles. Compatible history and track identities are retained. A rebuild failure warns after the main device change; it does not undo that completed change.
