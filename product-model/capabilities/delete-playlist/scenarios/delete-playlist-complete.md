---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ confirms deletion of a local list.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::playlist
- text: The Product removes the playlist and its membership while keeping library audio.
  kind: product
  entities:
  - entity: playlist
    effect: removes
  actor: dj
  contexts:
    desktop:
      place: desktop::playlist
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
---

# Delete playlist

## Trigger

The DJ confirms deletion of a local list.

## Outcome

The Product removes the playlist and its membership while keeping library audio.
