---
kind: alternate
routes:
  desktop: Desktop app
steps:
- text: The DJ changes genre, rating or release date and saves.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::cue-editor
- text: The Product saves the USB track changes and mirrors them to its resolved local track; affected playlist
    export indicators are cleared.
  kind: product
  entities:
  - entity: usb-track
    effect: changes
    facts:
    - Genre
    - Rating
    - Release date
  - entity: track
    effect: changes
    facts:
    - Genre
    - Rating
    - Release date
  - entity: playlist
    effect: changes
    facts:
    - Last export
  actor: dj
  contexts:
    desktop:
      place: desktop::cue-editor
references:
- kind: code
  role: implementation
  target: backend/src/service/track_metadata.rs
- kind: code
  role: implementation
  target: vanilla-ui/components/shared/track_metadata_edits.mjs
- kind: spec
  role: intent
  target: docs/CUE_EDITOR.md
---

# Edit track metadata directly on USB

## Trigger

The editor was opened from a USB playlist or history recording with a resolved local match.

## Outcome

With a resolved local match, saved changes reach the USB immediately and that local recording; no playlist re-export is required.

## Edge cases

- A disconnected drive or missing required database entry blocks the save.
- Metadata saves leave existing cue and grid information unchanged.
