---
availability:
- place: desktop
references:
- kind: code
  role: implementation
  target: backend/src/service/playback.rs#play_resolved_track
- kind: code
  role: implementation
  target: backend/src/service/playback.rs#resolve_playback_source
- kind: code
  role: implementation
  target: vanilla-ui/components/playback/actions.mjs
- kind: spec
  role: intent
  target: docs/PLAYLISTS_PLAYBACK.md
---

# Play track

Listen using the native audio engine from any recording list or the Cue Editor.
