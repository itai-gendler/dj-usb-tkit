---
availability:
- place: desktop
references:
- kind: code
  role: implementation
  target: backend/src/service/playlists.rs#delete_playlist
- kind: code
  role: implementation
  target: vanilla-ui/components/playlist/actions.mjs
- kind: spec
  role: intent
  target: docs/PLAYLISTS_PLAYBACK.md
domain: playlists
---

# Delete playlist

Delete an app playlist; its recordings stay in the library.
