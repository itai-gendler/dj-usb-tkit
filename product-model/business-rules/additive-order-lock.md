---
appliesTo:
- type: entity
  id: playlist
- type: capability
  id: reorder-playlist-tracks
references:
- kind: code
  role: implementation
  target: backend/src/service/export.rs#playlist_locks_reorder_on_export
- kind: spec
  role: intent
  target: docs/PLAYLISTS_PLAYBACK.md
---

# Additive export locks manual ordering for an existing device list

Additive mode with a same-name list already on the selected USB locks local drag and column ordering because subsequent export preserves the device order.
