---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ changes a cue position, label or colour and saves.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::cue-editor
- text: The Product stores the edited cue list and retains the other recording values.
  kind: product
  entities:
  - entity: track
    effect: changes
    facts:
    - Hot cues
    - Memory cues
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

# Edit cue in the library

## Trigger

The DJ changes a cue position, label or colour and saves.

## Outcome

The Product stores the edited cue list and retains the other recording values.

## Edge cases

- Undo and redo adjust unsaved edits; closing with unsaved changes requires an explicit decision.
- A cue placed past the known end of the audio is saved at the end; hot cues are limited to eight.
