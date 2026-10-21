---
kind: edge
routes:
  desktop: Desktop app
steps:
- text: The DJ chooses the external list.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::playlist
- text: The Product reports that no entries can be imported.
  kind: product
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::playlist
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
---

# Refuse an entirely unavailable list

## Trigger

None of the chosen list entries has importable audio.

## Outcome

No empty playlist is created and partial local track writes are rolled back.
