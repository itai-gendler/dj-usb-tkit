---
kind: validation
routes:
  desktop: Desktop app
steps:
- text: The DJ submits an order.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::playlist
- text: The Product rejects the incomplete or duplicate order for the playlist.
  kind: product
  entities:
  - entity: playlist
    effect: reads
    facts:
    - Name
    - Track order
    - Sidebar order
    - Import source
    - Last export
    - Reorder locked
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

# Reject an incomplete order

## Trigger

The requested full order omits, duplicates or introduces entries.

## Outcome

The saved order remains unchanged.
