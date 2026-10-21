---
appliesTo:
- type: entity
  id: playlist
- type: capability
  id: edit-cue
- type: capability
  id: edit-beat-grid
- type: capability
  id: edit-track-metadata
references:
- kind: code
  role: implementation
  target: backend/src/service/playlists.rs
- kind: code
  role: implementation
  target: backend/src/service/cues.rs#mark_track_edited_tx
- kind: spec
  role: intent
  target: docs/APP_DATA_MODEL.md
---

# Playlist changes invalidate the last-export indicator

Renaming, membership changes, saved reordering and saved recording edits clear the affected local lists' last-export metadata.
