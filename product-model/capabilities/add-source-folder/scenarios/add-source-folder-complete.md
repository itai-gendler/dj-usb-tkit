---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ chooses a music directory.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::library
- text: The Product remembers the source folder with enabled selection and availability, then indexes its supported
    audio.
  kind: product
  entities:
  - entity: source-folder
    effect: creates
    facts:
    - Path
    - Enabled
    - Availability
    - Analysis summary
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
  actor: dj
  contexts:
    desktop:
      place: desktop::library
references:
- kind: code
  role: implementation
  target: vanilla-ui/components/library/events.mjs
- kind: spec
  role: intent
  target: docs/LIBRARY_ANALYSIS.md
- kind: code
  role: implementation
  target: backend/src/service/library.rs#scan_library
---

# Add source folder

## Trigger

The DJ chooses a music directory.

## Outcome

The app remembers and indexes the new folder. Heavy analysis remains a separate preparation action.
