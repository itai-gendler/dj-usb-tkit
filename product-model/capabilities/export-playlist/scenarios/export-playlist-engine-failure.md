---
kind: edge
routes:
  desktop: Desktop app
steps:
- text: The DJ chooses Export for the prepared list.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::playlist
- text: The Product reads playlist membership, track analysis and settings, and commits any pending local order.
  kind: product
  entities:
  - entity: playlist
    effect: reads
    facts:
    - Name
    - Tracks
    - Sidebar order
    - Import source
    - Last export
    - Reorder locked
  - entity: track
    effect: reads
    facts:
    - File
    - Duration
    - BPM
    - First beat
    - Waveform
    - Hot cues
    - Memory cues
    - Playback start
  - entity: settings
    effect: reads
    facts:
    - Sync mode
    - Backup before export
    - Write Engine DJ library
  actor: dj
  contexts:
    desktop:
      place: desktop::playlist
- text: The Product writes USB playlist membership, USB track media and analysis, and records playlist last export.
  kind: product
  entities:
  - entity: usb-playlist
    effect: changes
    facts:
    - Name
    - Tracks
    - Menu order
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
  - entity: playlist
    effect: changes
    facts:
    - Last export
  actor: dj
  contexts:
    desktop:
      place: desktop::playlist
- text: The Product reports the USB device Engine DJ rebuild warning.
  kind: product
  entities:
  - entity: usb-device
    effect: reads
    facts:
    - Root
    - Name
    - Writable
    - Structure
    - Last seen
    - Database contents
    - Engine DJ library
    - Diagnostics
    - Parity
  actor: dj
  contexts:
    desktop:
      place: desktop::playlist
references:
- kind: code
  role: implementation
  target: backend/src/service/engine_export.rs#refresh_engine_library
- kind: spec
  role: intent
  target: docs/ENGINE_DJ.md
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

# Keep the completed device change when optional output fails

## Trigger

The main USB change has completed but Engine DJ rebuilding fails.

## Outcome

A warning reports that optional output was not written; the prior device change remains completed.
