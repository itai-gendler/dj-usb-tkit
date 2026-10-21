---
kind: primary
routes:
  library: Media Library
  playlist: App playlist
  usb: USB playlist
  history: USB history
  editor: Cue Editor
steps:
- text: The DJ chooses Resume.
  kind: actor
  entities: []
  actor: dj
  contexts:
    library:
      place: desktop::library
    playlist:
      place: desktop::playlist
    usb:
      place: desktop::usb
    history:
      place: desktop::history
    editor:
      place: desktop::cue-editor
- text: The Product changes playback state and reports the current position.
  kind: product
  entities:
  - entity: playback
    effect: changes
    from: Paused
    to: Playing
    facts:
    - Position
  actor: dj
  contexts:
    library:
      place: desktop::library
    playlist:
      place: desktop::playlist
    usb:
      place: desktop::usb
    history:
      place: desktop::history
    editor:
      place: desktop::cue-editor
references:
- kind: code
  role: implementation
  target: backend/src/service/playback.rs
- kind: spec
  role: intent
  target: docs/PLAYLISTS_PLAYBACK.md
---

# Resume playback

## Trigger

The DJ chooses Resume playback.

## Outcome

The Product changes playback state and reports the current position.
