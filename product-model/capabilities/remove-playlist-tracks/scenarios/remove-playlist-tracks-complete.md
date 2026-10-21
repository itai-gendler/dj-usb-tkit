---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ selects entries to remove from the current list.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::playlist
- text: The Product removes those entries from the playlist, keeps the remaining order, and clears last export; the tracks
    stay in the library.
  kind: product
  entities:
  - entity: playlist
    effect: changes
    facts:
    - Tracks
    - Last export
    - Track order
  - entity: track
    effect: reads
    facts: []
  actor: dj
  contexts:
    desktop:
      place: desktop::playlist
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
---

# Remove playlist tracks

## Trigger

The DJ selects entries to remove from the current list.

## Outcome

The Product removes those entries from the playlist, keeps the remaining order, and clears last export; the tracks stay in the library.
