---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ edits the beat grid or musical key and saves.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::cue-editor
- text: The Product stores user-owned analysis values and rewrites available analysis data. Cues retain audio positions
    unless Cues follow grid was enabled during the edit.
  kind: product
  entities:
  - entity: track
    effect: changes
    facts:
    - BPM
    - Key
    - First beat
    - Hot cues
    - Memory cues
    - Playback start
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
  target: backend/src/service/cues.rs
- kind: code
  role: implementation
  target: vanilla-ui/components/track-detail/actions.mjs
- kind: spec
  role: intent
  target: docs/CUE_EDITOR.md
---

# Edit beat grid in the library

## Trigger

The DJ edits the beat grid or musical key and saves.

## Outcome

The Product stores user-owned analysis values and rewrites available analysis data. Cues retain audio positions unless Cues follow grid was enabled during the edit.

## Edge cases

- Undo and redo adjust unsaved edits; closing with unsaved changes requires an explicit decision.
