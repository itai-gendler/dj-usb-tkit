---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ opens a local list and chooses a search or sort.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::playlist
- text: The Product presents playlist membership, last export and matching tracks, with whole-filter counts and duration.
  kind: product
  entities:
  - entity: playlist
    effect: reads
    facts:
    - Name
    - Tracks
    - Sidebar order
    - Import source
    - Last export
    - Reorder locked
  - entity: track
    effect: reads
    facts:
    - Title
    - Artist
    - Album
    - File
    - Duration
    - BPM
    - Key
    - Waveform
    - Artwork
    - Genre
    - Release date
  actor: dj
  contexts:
    desktop:
      place: desktop::playlist
references:
- kind: code
  role: implementation
  target: backend/src/service/playlists.rs#get_playlist_tracks
- kind: code
  role: implementation
  target: vanilla-ui/components/playlist/actions.mjs
- kind: spec
  role: intent
  target: docs/PLAYLISTS_PLAYBACK.md
---

# Browse playlist

## Trigger

The DJ opens a local list and chooses a search or sort.

## Outcome

The Product presents playlist membership, last export and matching tracks, with whole-filter counts and duration.
