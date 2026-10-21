---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ loads device sessions and selects one.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::history
- text: The Product presents USB history names, dates, counts and ordered USB tracks with on-demand previews.
  kind: product
  entities:
  - entity: usb-history
    effect: reads
    facts:
    - Name
    - Date
    - Tracks
    - Count
  - entity: usb-track
    effect: reads
    facts:
    - Title
    - Artist
    - Album
    - Media
    - Duration
    - BPM
    - Key
    - Waveform
    - Artwork
    - Local match
    - Genre
    - Release date
  actor: dj
  contexts:
    desktop:
      place: desktop::history
references:
- kind: code
  role: implementation
  target: backend/src/service/usb.rs#fetch_usb_histories_with_progress
- kind: code
  role: implementation
  target: backend/src/service/usb.rs#fetch_usb_history_tracks
- kind: spec
  role: intent
  target: docs/USB_IMPORT.md
---

# Browse USB history

## Trigger

The DJ loads device sessions and selects one.

## Outcome

The Product presents USB history names, dates, counts and ordered USB tracks with on-demand previews.

## Edge cases

- Dates can be estimated and are not guaranteed hardware playback timestamps.
