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
  text: The DJ changes a cue position, label or colour and saves.
- actor: dj
  contexts:
    desktop:
      place: desktop::cue-editor
  entities:
  - effect: changes
    entity: usb-track
    facts:
    - Hot cues
    - Memory cues
  kind: product
  text: The Product saves the USB track values on the selected drive and reports that no local counterpart was changed.
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

# Edit a cue on a recording that is only on the USB

## Trigger

The chosen device recording has no resolved local counterpart.

## Outcome

The direct device edit succeeds and reports that the local library was not changed.
