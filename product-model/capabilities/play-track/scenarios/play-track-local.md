---
kind: primary
routes:
  library: Media Library
  playlist: App playlist
  usb: USB playlist
  history: USB history
  editor: Cue Editor
steps:
- text: The DJ chooses Play.
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
- text: The Product resolves the track to available local audio and starts playback.
  kind: product
  entities:
  - entity: track
    effect: reads
    facts:
    - File
  - entity: playback
    effect: changes
    from: Stopped
    to: Playing
    facts:
    - Recording
    - Source
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

# Play the available local recording

## Trigger

The DJ starts playback.

## Outcome

The native session plays the selected available local file and reports position.
