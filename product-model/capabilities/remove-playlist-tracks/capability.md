---
availability:
- place: desktop
references:
- kind: code
  role: implementation
  target: backend/src/service/playlists.rs#remove_tracks_from_playlist
- kind: code
  role: implementation
  target: vanilla-ui/components/playlist/actions.mjs
- kind: spec
  role: intent
  target: docs/PLAYLISTS_PLAYBACK.md
domain: playlists
---

# Remove playlist tracks

Take selected recordings out of an app playlist.
