---
availability:
- place: desktop
references:
- kind: code
  role: implementation
  target: backend/src/service/playlists.rs#reorder_playlist_tracks
- kind: code
  role: implementation
  target: vanilla-ui/components/playlist/actions.mjs
- kind: spec
  role: intent
  target: docs/PLAYLISTS_PLAYBACK.md
domain: playlists
---

# Reorder playlist tracks

Save a new order for an app playlist's recordings, by dragging or by keeping a column sort.
