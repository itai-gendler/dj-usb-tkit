---
appliesTo:
- type: entity
  id: playlist
references:
- kind: code
  role: implementation
  target: backend/src/service/playlists.rs
- kind: spec
  role: intent
  target: docs/PLAYLISTS_PLAYBACK.md
---

# Playlist membership contains each recording once

Adding a selection skips recordings already present. Saved ordering spans the complete current membership; local sidebar order and device menu order remain independent.
