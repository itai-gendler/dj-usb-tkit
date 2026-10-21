---
kind: edge
routes:
  desktop: Desktop app
steps:
- text: The DJ requests Export.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::playlist
- text: The Product reads additive settings and checks source availability.
  kind: product
  entities:
  - entity: settings
    effect: reads
    facts:
    - Sync mode
  - entity: track
    effect: reads
    facts:
    - File
  actor: dj
  contexts:
    desktop:
      place: desktop::playlist
- text: The Product appends available USB tracks to the USB playlist and records playlist last export.
  kind: product
  entities:
  - entity: usb-track
    effect: changes
    facts:
    - Title
    - Artist
    - Album
    - Media
    - Duration
    - BPM
    - Key
    - First beat
    - Waveform
    - Artwork
    - Hot cues
    - Memory cues
    - Playback start
    - Genre
    - Rating
    - Release date
    - Local match
  - entity: usb-playlist
    effect: changes
    facts:
    - Tracks
    - Menu order
  - entity: playlist
    effect: changes
    facts:
    - Last export
  actor: dj
  contexts:
    desktop:
      place: desktop::playlist
references:
- kind: code
  role: implementation
  target: backend/src/service/export.rs#export_to_usb_with_progress
- kind: code
  role: implementation
  target: backend/src/service/export.rs#run_manifest_invariant_check
- kind: code
  role: implementation
  target: vanilla-ui/components/usb/actions.mjs#exportPlaylistToUsb
- kind: spec
  role: intent
  target: docs/USB_EXPORT.md
---

# Append the available subset

## Trigger

Individual source files are missing and additive mode is selected.

## Outcome

Available recordings append with skipped counts and warnings; existing membership remains.

## Edge cases

- If no recordings are exportable, the request fails rather than writing an empty result.
