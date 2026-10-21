---
kind: alternate
routes:
  desktop: Desktop app
steps:
- text: The DJ chooses Stop.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::cue-editor
- text: The Product stops playback.
  kind: product
  entities:
  - entity: playback
    effect: changes
    from: Paused
    to: Stopped
    facts:
    - Position
  actor: dj
  contexts:
    desktop:
      place: desktop::cue-editor
references:
- kind: code
  role: implementation
  target: backend/src/service/playback.rs
- kind: spec
  role: intent
  target: docs/PLAYLISTS_PLAYBACK.md
---

# Stop a held recording

## Trigger

Audio is paused.

## Outcome

The native session stops and the transport resets.
