---
kind: primary
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
- text: The Product stores only the changed descriptive values, leaving cues and beat grid intact.
  kind: product
  entities:
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

# Edit track metadata in the library

## Trigger

The DJ changes genre, rating or release date and saves.

## Outcome

The Product stores only the changed descriptive values, leaving cues and beat grid intact.

## Edge cases

- Blank genre or release date clears it; rating zero clears the stars.
- Mixed bulk values change only where the DJ supplied an edit.
- Invalid dates and ratings outside zero to five are rejected.
