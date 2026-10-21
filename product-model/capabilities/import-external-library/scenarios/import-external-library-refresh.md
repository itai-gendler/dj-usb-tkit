---
kind: alternate
routes:
  desktop: Desktop app
steps:
- text: The DJ imports the detected source again.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::library
- text: The Product refreshes track text and eligible imported values, leaving user-owned values and existing cue
    lists intact.
  kind: product
  entities:
  - entity: track
    effect: changes
    facts:
    - Title
    - Artist
    - Album
    - Genre
    - BPM
    - Key
    - First beat
    - Duration
    - Artwork
    - Waveform
    - Sources
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

# Refresh an existing import

## Trigger

The DJ imports the same source again.

## Outcome

Existing recordings are updated according to field ownership; local edits and existing cues are retained.
