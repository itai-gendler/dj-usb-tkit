---
kind: validation
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
- text: The Product reports the playlist missing-analysis count after checking its tracks.
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
    - Duration
    - BPM
    - Waveform
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

# Request analysis before export

## Trigger

Some selected recordings lack required analysis or bundle files.

## Outcome

Export is rejected before media copy and the app directs the DJ to Analyze Missing Tracks.
