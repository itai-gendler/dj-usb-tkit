---
availability:
- place: desktop
references:
- kind: code
  role: implementation
  target: backend/src/service/rekordbox_import.rs#import_rekordbox_playlist
- kind: code
  role: implementation
  target: backend/src/service/mixxx_import.rs#import_mixxx_playlist
- kind: code
  role: implementation
  target: backend/src/service/playlists.rs#save_imported_playlist
- kind: code
  role: implementation
  target: vanilla-ui/components/playlist/actions.mjs#importExternalPlaylist
- kind: spec
  role: intent
  target: docs/EXTERNAL_LIBRARIES.md
domain: playlists
---

# Import external playlist

Choose a non-empty external playlist, history or Mixxx crate and prepare it as a local playlist.
