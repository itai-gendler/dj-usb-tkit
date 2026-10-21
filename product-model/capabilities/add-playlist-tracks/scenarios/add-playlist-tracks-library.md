---
kind: alternate
routes:
  desktop: Desktop app
steps:
- text: The DJ chooses one or more destination lists.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::library
- text: The Product adds each selected recording that a chosen list does not hold yet to the end of that list.
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
      place: desktop::library
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

# Add selected recordings from Media Library

## Trigger

The DJ selects recordings in Media Library.

## Outcome

The chosen lists receive each resolved recording at most once.
