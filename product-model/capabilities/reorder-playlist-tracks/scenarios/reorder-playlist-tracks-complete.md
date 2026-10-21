---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ moves an entry or commits the current column sort.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::playlist
- text: The Product saves the complete playlist order and clears last export.
  kind: product
  entities:
  - entity: playlist
    effect: changes
    facts:
    - Track order
    - Last export
  actor: dj
  contexts:
    desktop:
      place: desktop::playlist
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
---

# Reorder playlist tracks

## Trigger

The DJ moves an entry or commits the current column sort.

## Outcome

The Product saves the complete playlist track order and clears last export.
