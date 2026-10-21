---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ chooses sources and a search or sort.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::library
- text: The Product saves source folder and imported external library enabled filters.
  kind: product
  actor: dj
  entities:
  - entity: source-folder
    effect: changes
    facts:
    - Enabled
  - entity: external-library
    effect: changes
    facts:
    - Enabled
  contexts:
    desktop:
      place: desktop::library
- text: The Product presents matching tracks, source folder status and external library selections, with counts and duration
    over the filtered collection.
  kind: product
  entities:
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
    - Sources
    - Genre
    - Release date
  - entity: source-folder
    effect: reads
    facts:
    - Path
    - Enabled
    - Availability
    - Analysis summary
  - entity: external-library
    effect: reads
    facts:
    - Application
    - Location
    - Imported
    - Enabled
    - Lists
  actor: dj
  contexts:
    desktop:
      place: desktop::library
references:
- kind: code
  role: implementation
  target: backend/src/service/library.rs#browse_source_files
- kind: code
  role: implementation
  target: vanilla-ui/components/library/actions.mjs
- kind: spec
  role: intent
  target: docs/LIBRARY_ANALYSIS.md
---

# Browse library

## Trigger

The DJ chooses sources and a search or sort.

## Outcome

The Product presents matching tracks, source folder status and external library selections, with counts and duration over the filtered collection.

## Edge cases

- Disabling a source filter hides its recordings without deleting or reimporting them.
- A track with both external origins appears when either imported source is enabled.
