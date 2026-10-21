---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ supplies a replacement name.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::playlist
- text: The Product changes the playlist name and clears last export.
  kind: product
  entities:
  - entity: playlist
    effect: changes
    facts:
    - Name
    - Last export
  actor: dj
  contexts:
    desktop:
      place: desktop::playlist
references:
- kind: code
  role: implementation
  target: backend/src/service/playlists.rs#rename_playlist
- kind: code
  role: implementation
  target: vanilla-ui/components/playlist/actions.mjs
- kind: spec
  role: intent
  target: docs/PLAYLISTS_PLAYBACK.md
---

# Rename playlist

## Trigger

The DJ supplies a replacement name.

## Outcome

The Product changes the playlist name and clears last export.
