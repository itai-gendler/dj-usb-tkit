---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ adds a hot cue or memory cue at the chosen audio position and saves.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::cue-editor
- text: The Product stores the new cue position with its label and colour. Hot cues take pads in time order; memory
    cues use no pad.
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

# Add cue in the library

## Trigger

The DJ adds a hot cue or memory cue at the chosen audio position and saves.

## Outcome

The Product stores the new cue position with its label and colour. Hot cues take pads in time order; memory cues use no pad.

## Edge cases

- Undo and redo adjust unsaved edits; closing with unsaved changes requires an explicit decision.
- A cue placed past the known end of the audio is saved at the end; hot cues are limited to eight.
