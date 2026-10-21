---
kind: alternate
routes:
  desktop: Desktop app
steps:
- text: The DJ removes a cue and saves.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::cue-editor
- text: The Product saves the USB track changes and mirrors them to its resolved local track; affected playlist
    export indicators are cleared.
  kind: product
  entities:
  - entity: usb-track
    effect: changes
    facts:
    - Hot cues
    - Memory cues
    - Playback start
  - entity: track
    effect: changes
    facts:
    - Hot cues
    - Memory cues
    - Playback start
  - entity: playlist
    effect: changes
    facts:
    - Last export
  actor: dj
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

# Remove cue directly on USB

## Trigger

The editor was opened from a USB playlist or history recording with a resolved local match.

## Outcome

With a resolved local match, saved changes reach the USB immediately and that local recording; no playlist re-export is required.

## Edge cases

- A disconnected drive, missing required analysis bundle or missing required database entry blocks the save.
- An analysis-only USB save leaves existing cue chunks untouched unless the cue list was edited.
