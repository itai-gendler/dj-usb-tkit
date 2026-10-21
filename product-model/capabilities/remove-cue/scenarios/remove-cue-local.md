---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ removes a cue and saves.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::cue-editor
- text: The Product stores the remaining cue positions; removing every cue also removes the start marker.
  kind: product
  entities:
  - entity: track
    effect: changes
    facts:
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

# Remove cue in the library

## Trigger

The DJ removes a cue and saves.

## Outcome

The Product stores the remaining cue positions; when no other cue is left, the playback start goes too.

## Edge cases

- Undo and redo adjust unsaved edits; closing with unsaved changes requires an explicit decision.
