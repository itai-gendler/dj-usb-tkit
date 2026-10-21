---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ chooses another audio position.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::cue-editor
- text: The Product moves playback to the chosen position; with no active audio it loads paused for a later Play.
  kind: product
  entities:
  - entity: playback
    effect: changes
    facts:
    - Position
  actor: dj
  contexts:
    desktop:
      place: desktop::cue-editor
references:
- kind: code
  role: implementation
  target: vanilla-ui/components/track-detail/actions.mjs
- kind: code
  role: implementation
  target: backend/src/service/playback.rs#play_resolved_track
- kind: spec
  role: intent
  target: docs/CUE_EDITOR.md
---

# Seek playback

## Trigger

The DJ chooses another audio position.

## Outcome

The Product moves playback to the chosen position; with no active audio it loads paused for a later Play.
