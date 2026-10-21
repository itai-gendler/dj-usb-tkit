---
availability:
- place: desktop
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

Move the listening position while retaining the chosen playing or paused state.
