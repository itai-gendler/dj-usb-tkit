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
      place: desktop::usb
- text: The Product finds the matching library recording for each selection, adding one to the library for a recording only
    on the USB, and adds it to each chosen list that does not hold it yet.
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
    effect: changes
    facts:
    - Tracks
    - Last export
    - Track order
  actor: dj
  contexts:
    desktop:
      place: desktop::usb
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

# Add selected recordings from USB Browser

## Trigger

The DJ selects recordings in USB Browser.

## Outcome

The chosen lists receive each resolved recording at most once.
