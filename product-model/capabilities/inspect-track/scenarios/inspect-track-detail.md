---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ opens recording details.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::cue-editor
- text: The Product presents the track or USB track details for the selected origin.
  kind: product
  entities:
  - entity: track
    effect: reads
    facts:
    - Title
    - Artist
    - Album
    - Duration
    - BPM
    - Key
    - First beat
    - Waveform
    - Hot cues
    - Memory cues
    - Playback start
    - Genre
    - Rating
    - Release date
  - entity: usb-track
    effect: reads
    facts:
    - Title
    - Artist
    - Album
    - Duration
    - BPM
    - Key
    - First beat
    - Waveform
    - Hot cues
    - Memory cues
    - Playback start
    - Genre
    - Rating
    - Release date
  actor: dj
  contexts:
    desktop:
      place: desktop::cue-editor
references:
- kind: code
  role: implementation
  target: backend/src/service/cues.rs#get_track_detail
- kind: code
  role: implementation
  target: backend/src/service/cues.rs#get_usb_track_detail
- kind: code
  role: implementation
  target: vanilla-ui/components/track-detail/actions.mjs#openTrackDetail
- kind: spec
  role: intent
  target: docs/CUE_EDITOR.md
---

# Inspect recording detail

## Trigger

The DJ opens the detail view of an analyzed recording.

## Outcome

The full waveform, cue positions, grid and editable metadata are available.

## Edge cases

- The entry point is unavailable until the recording has analysis.
