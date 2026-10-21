---
kind: validation
routes:
  desktop: Desktop app
steps:
- text: The DJ submits the new cue list.
  kind: actor
  actor: dj
  entities: []
  contexts:
    desktop:
      place: desktop::cue-editor
- text: The Product reports the hot-cue limit without saving the new list.
  kind: product
  actor: dj
  entities: []
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

# Reject more than eight hot cues

## Trigger

The saved cue list would contain more than eight hot cues.

## Outcome

The save is rejected; memory cues do not count toward this limit.
