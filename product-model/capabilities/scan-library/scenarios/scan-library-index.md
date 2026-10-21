---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ requests a library scan.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::library
- text: The Product reads each available source folder and creates new tracks from supported audio.
  kind: product
  entities:
  - entity: source-folder
    effect: reads
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
    as: new-recording
  actor: dj
  contexts:
    desktop:
      place: desktop::library
- text: The Product refreshes existing track metadata under available source folders.
  kind: product
  entities:
  - entity: track
    effect: changes
    facts:
    - Title
    - Artist
    - Album
    - File
    - Genre
    - Release date
    as: indexed-recording
  - entity: source-folder
    effect: reads
    facts:
    - Path
    - Enabled
    - Availability
    - Analysis summary
  actor: dj
  contexts:
    desktop:
      place: desktop::library
- text: The Product removes stale tracks only under available source folders and removes their playlist membership.
  kind: product
  actor: dj
  entities:
  - entity: track
    effect: removes
    as: stale-recording
  - entity: source-folder
    effect: reads
    facts: []
  - entity: playlist
    effect: changes
    facts:
    - Tracks
    - Track order
  contexts:
    desktop:
      place: desktop::library
- text: The Product starts an analysis run for the recordings in the current selection that are missing analysis, and enriches
    each one as it goes.
  kind: product
  actor: dj
  entities:
  - entity: analysis-job
    effect: creates
    to: Running
    facts:
    - Selection
    - Progress
    - Results
  - entity: track
    effect: changes
    facts:
    - Duration
    - BPM
    - Key
    - First beat
    - Waveform
    - Artwork
    as: indexed-recording
  contexts:
    desktop:
      place: desktop::library
references:
- kind: code
  role: implementation
  target: backend/src/service/library.rs#scan_library
- kind: code
  role: implementation
  target: vanilla-ui/components/library/actions.mjs
- kind: spec
  role: intent
  target: docs/LIBRARY_ANALYSIS.md
---

# Index enabled folders

## Trigger

The DJ starts Scan Library.

## Outcome

Indexed rows appear before enrichment; the app starts missing analysis for the current selection.

## Edge cases

- Byte-identical copies are collapsed while preserving playlist membership.
- Unsupported files and per-file failures are reported while remaining files are processed.
