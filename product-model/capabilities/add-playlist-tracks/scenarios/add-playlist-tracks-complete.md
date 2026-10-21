---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ chooses selected recordings and one or more destination lists.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::playlist
- text: The Product resolves local track identities and appends distinct entries to each playlist, clearing last export.
  kind: product
  entities:
  - entity: track
    effect: reads
    facts: []
  - entity: playlist
    effect: changes
    facts:
    - Tracks
    - Last export
    - Track order
  actor: dj
  contexts:
    desktop:
      place: desktop::playlist
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
---

# Add playlist tracks

## Trigger

The DJ chooses selected recordings and one or more destination lists.

## Outcome

The Product resolves local track identities and appends distinct entries to each playlist, clearing last export.
