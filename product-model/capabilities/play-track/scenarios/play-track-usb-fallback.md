---
kind: alternate
routes:
  desktop: Desktop app
steps:
- text: The DJ chooses Play for a device recording.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::usb
- text: The Product resolves the USB track and starts playback from the selected drive.
  kind: product
  entities:
  - entity: usb-track
    effect: reads
    facts:
    - Media
    - Local match
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
    desktop:
      place: desktop::usb
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

# Use USB audio when local playback is unavailable

## Trigger

A USB recording has no usable local match, or its matched local file fails to play.

## Outcome

The selected drive supplies the audio and the displayed source says USB.
