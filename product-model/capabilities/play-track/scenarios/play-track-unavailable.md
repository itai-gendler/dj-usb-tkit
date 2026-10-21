---
kind: edge
routes:
  desktop: Desktop app
steps:
- text: The DJ chooses Play.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::cue-editor
- text: The Product reports that audio could not be played.
  kind: product
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::cue-editor
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

# Report unavailable audio

## Trigger

Neither library nor selected USB provides playable audio.

## Outcome

The request reports an error instead of starting another recording.
