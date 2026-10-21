---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ sets the metronome and listening balance.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::cue-editor
- text: The Product changes playback click enablement, grid and music balance.
  kind: product
  entities:
  - entity: playback
    effect: changes
    facts:
    - Metronome
  actor: dj
  contexts:
    desktop:
      place: desktop::cue-editor
references:
- kind: code
  role: implementation
  target: backend/src/service/playback.rs#set_playback_metronome
- kind: code
  role: implementation
  target: vanilla-ui/components/track-detail/actions.mjs
- kind: spec
  role: intent
  target: docs/CUE_EDITOR.md
---

# Change metronome settings

## Trigger

The DJ sets the metronome and listening balance.

## Outcome

The Product changes playback metronome settings for the current grid.

## Edge cases

- Clicks start disabled whenever the editor opens and stop when it closes. The chosen music/click balance is remembered.
