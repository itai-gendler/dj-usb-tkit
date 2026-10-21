---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ supplies a non-empty name.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::playlist
- text: The Product creates an empty playlist at the top of the local list and opens it.
  kind: product
  entities:
  - entity: playlist
    effect: creates
    facts:
    - Name
    - Tracks
    - Sidebar order
    - Import source
    - Last export
    - Reorder locked
    - Track order
  actor: dj
  contexts:
    desktop:
      place: desktop::playlist
references:
- kind: code
  role: implementation
  target: backend/src/service/playlists.rs#create_playlist
- kind: code
  role: implementation
  target: vanilla-ui/components/playlist/actions.mjs
- kind: spec
  role: intent
  target: docs/PLAYLISTS_PLAYBACK.md
---

# Create playlist

## Trigger

The DJ supplies a non-empty name.

## Outcome

The Product creates an empty playlist at the top of the local list and opens it.
