---
kind: alternate
routes:
  desktop: Desktop app
steps:
- actor: dj
  contexts:
    desktop:
      place: desktop::cue-editor
  entities: []
  kind: actor
  text: The DJ changes genre, rating or release date and saves.
- actor: dj
  contexts:
    desktop:
      place: desktop::cue-editor
  entities:
  - effect: changes
    entity: usb-track
    facts:
    - Genre
    - Rating
    - Release date
  kind: product
  text: The Product saves the USB track values on the selected drive and reports that no local counterpart was changed.
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

# Edit metadata of a recording that is only on the USB

## Trigger

The chosen device recording has no resolved local counterpart.

## Outcome

The direct device edit succeeds and reports that the local library was not changed.
