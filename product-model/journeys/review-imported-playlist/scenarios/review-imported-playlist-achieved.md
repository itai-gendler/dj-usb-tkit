---
kind: primary
result: achieved
routes:
  desktop: Desktop app
steps:
- text: The DJ selects an external list to import.
  kind: actor
  entities: []
  capability: import-external-playlist
  actor: dj
  contexts:
    desktop:
      place: desktop::playlist
- text: The Product imports tracks, creates the playlist and opens it.
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
  capability: import-external-playlist
  actor: dj
  contexts:
    desktop:
      place: desktop::playlist
- text: The DJ inspects the opened list.
  kind: actor
  entities: []
  capability: browse-playlist
  actor: dj
  contexts:
    desktop:
      place: desktop::playlist
- text: The Product presents playlist membership and track information.
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
    - Track order
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
  capability: browse-playlist
  actor: dj
  contexts:
    desktop:
      place: desktop::playlist
references:
- kind: code
  role: implementation
  target: vanilla-ui/components/playlist/actions.mjs#importExternalPlaylist
---

# Review an imported playlist

## Trigger

The DJ selects an external list to prepare locally.

## Outcome

The imported list is opened with its resolved recordings and source information.
