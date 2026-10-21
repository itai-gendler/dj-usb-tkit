---
kind: validation
routes:
  desktop: Desktop app
steps:
- text: The DJ submits corrected tempo or grid values.
  kind: actor
  actor: dj
  entities: []
  contexts:
    desktop:
      place: desktop::cue-editor
- text: The Product rejects the invalid values before saving.
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

# Reject invalid beat-grid values

## Trigger

The supplied BPM is outside the supported positive range or the first beat is beyond the known duration.

## Outcome

The save is rejected with the invalid field identified.
