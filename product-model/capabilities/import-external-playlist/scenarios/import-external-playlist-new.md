---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ chooses an external list and whether to force its metadata.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::playlist
- text: The Product imports available tracks and creates the playlist with deduplicated membership.
  kind: product
  entities:
  - entity: track
    effect: creates
    facts:
    - Title
    - Artist
    - Album
    - File
    - Duration
    - BPM
    - Key
    - First beat
    - Waveform
    - Artwork
    - Sources
    - Hot cues
    - Memory cues
    - Playback start
    - Genre
    - Rating
    - Release date
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
- text: The Product opens the playlist for preparation and enables the external library selection.
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
  - entity: external-library
    effect: changes
    facts:
    - Imported
    - Enabled
  actor: dj
  contexts:
    desktop:
      place: desktop::playlist
references:
- kind: code
  role: implementation
  target: backend/src/service/rekordbox_import.rs#import_rekordbox_playlist
- kind: code
  role: implementation
  target: backend/src/service/mixxx_import.rs#import_mixxx_playlist
- kind: code
  role: implementation
  target: backend/src/service/playlists.rs#save_imported_playlist
- kind: code
  role: implementation
  target: vanilla-ui/components/playlist/actions.mjs#importExternalPlaylist
- kind: spec
  role: intent
  target: docs/EXTERNAL_LIBRARIES.md
---

# Import and open a list

## Trigger

The DJ chooses Import and selects an external list.

## Outcome

The imported playlist opens with its source order; Mixxx crates use artist/title order.

## Edge cases

- rekordbox smart playlists and empty lists are not offered.
