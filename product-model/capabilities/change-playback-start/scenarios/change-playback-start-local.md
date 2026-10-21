---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ chooses where the player loads the recording and saves.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::cue-editor
- text: The Product stores the optional memory-only start position, never after the first hot cue.
  kind: product
  entities:
  - entity: track
    effect: changes
    facts:
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

# Change playback start in the library

## Trigger

The DJ chooses the playback start and saves.

## Outcome

The Product stores the optional memory-only start position, never after the first hot cue.

## Edge cases

- Undo and redo adjust unsaved edits; closing with unsaved changes requires an explicit decision.
- A start placed after the first hot cue is moved back to it; with no other cue left, the start is not kept.
