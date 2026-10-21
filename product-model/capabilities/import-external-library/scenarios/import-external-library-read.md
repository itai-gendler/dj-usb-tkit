---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ chooses the detected application to import.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::library
- text: The Product reads the external library and creates tracks with imported metadata, cues and available analysis.
  kind: product
  entities:
  - entity: external-library
    effect: reads
    facts:
    - Application
    - Location
    - Imported
    - Enabled
    - Lists
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
- text: The Product marks the external library imported and enabled.
  kind: product
  entities:
  - entity: external-library
    effect: changes
    facts:
    - Imported
    - Enabled
  actor: dj
  contexts:
    desktop:
      place: desktop::library
references:
- kind: code
  role: implementation
  target: backend/src/service/rekordbox_import.rs#scan_rekordbox_db
- kind: code
  role: implementation
  target: backend/src/service/mixxx_import.rs#scan_mixxx_db
- kind: spec
  role: intent
  target: docs/EXTERNAL_LIBRARIES.md
---

# Import available recordings

## Trigger

A local DJ library is detected.

## Outcome

Available supported recordings are indexed; source databases remain unchanged.

## Edge cases

- Missing files and externally deleted or unsupported recordings are skipped with reasons.
- Mixxx waveforms need local analysis; rekordbox analysis files can be reused.
