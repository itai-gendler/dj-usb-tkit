---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ chooses a new local list order.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::playlist
- text: The Product saves playlist sidebar order without changing device ordering.
  kind: product
  entities:
  - entity: playlist
    effect: changes
    facts:
    - Sidebar order
  actor: dj
  contexts:
    desktop:
      place: desktop::playlist
references:
- kind: code
  role: implementation
  target: backend/src/service/playlists.rs#reorder_playlists
- kind: code
  role: implementation
  target: vanilla-ui/components/playlist/actions.mjs
- kind: spec
  role: intent
  target: docs/PLAYLISTS_PLAYBACK.md
---

# Reorder playlists

## Trigger

The DJ chooses a new local list order.

## Outcome

The Product saves playlist sidebar order without changing device ordering.
