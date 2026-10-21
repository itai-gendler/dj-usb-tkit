---
availability:
- place: desktop
references:
- kind: code
  role: implementation
  target: backend/src/service/playlists.rs#add_tracks_to_playlist
- kind: code
  role: implementation
  target: vanilla-ui/components/playlist/actions.mjs
- kind: spec
  role: intent
  target: docs/PLAYLISTS_PLAYBACK.md
domain: playlists
---

# Add playlist tracks

Add selected recordings from the library, a USB playlist or USB history to one or more app playlists.
