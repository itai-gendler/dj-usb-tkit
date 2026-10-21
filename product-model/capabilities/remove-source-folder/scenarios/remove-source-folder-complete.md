---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ confirms removal of a configured directory.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::library
- text: The Product removes the source folder and indexed tracks no remaining configured folder covers; playlist
    membership for removed tracks disappears, while audio files remain.
  kind: product
  entities:
  - entity: source-folder
    effect: removes
  - entity: track
    effect: removes
  - entity: playlist
    effect: changes
    facts:
    - Tracks
    - Track order
  actor: dj
  contexts:
    desktop:
      place: desktop::library
references:
- kind: code
  role: implementation
  target: backend/src/service/source_roots.rs#remove_tracks_by_source_roots
- kind: code
  role: implementation
  target: vanilla-ui/components/library/events.mjs
- kind: spec
  role: intent
  target: docs/LIBRARY_ANALYSIS.md
---

# Remove source folder

## Trigger

The DJ confirms removal of a configured directory.

## Outcome

The Product removes the source folder and indexed tracks no remaining configured folder covers; playlist membership for removed tracks disappears, while audio files remain.

## Edge cases

- Cancelling confirmation preserves the configured sources and indexed music.
- Removing an overlapping parent or child leaves recordings still covered by another configured source.
