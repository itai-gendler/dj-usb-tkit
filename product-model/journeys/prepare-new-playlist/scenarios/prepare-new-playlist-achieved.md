---
kind: primary
result: achieved
routes:
  desktop: Desktop app
steps:
- text: The DJ creates a named list.
  kind: actor
  entities: []
  capability: create-playlist
  actor: dj
  contexts:
    desktop:
      place: desktop::playlist
- text: The Product creates the playlist and opens its preparation view.
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
  capability: create-playlist
  actor: dj
  contexts:
    desktop:
      place: desktop::playlist
- text: The DJ adds selected recordings to the opened list.
  kind: actor
  entities: []
  capability: add-playlist-tracks
  actor: dj
  contexts:
    desktop:
      place: desktop::playlist
- text: The Product adds distinct tracks to playlist membership.
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
  capability: add-playlist-tracks
  actor: dj
  contexts:
    desktop:
      place: desktop::playlist
references:
- kind: code
  role: implementation
  target: vanilla-ui/components/playlist/actions.mjs#createPlaylist
---

# Prepare a new playlist

## Trigger

The DJ creates a list to prepare music.

## Outcome

The created list is opened and receives the selected recordings.
