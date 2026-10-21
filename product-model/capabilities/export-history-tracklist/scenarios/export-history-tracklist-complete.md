---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ chooses the starting recording, optional cumulative times and output file.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::history
- text: The Product reads USB history and USB track durations and saves artist/title lines beginning at the chosen entry.
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
    - Duration
  actor: dj
  contexts:
    desktop:
      place: desktop::history
references:
- kind: code
  role: implementation
  target: vanilla-ui/components/usb/actions.mjs
- kind: code
  role: implementation
  target: vanilla-ui/track_utils.mjs#buildTracklistText
- kind: spec
  role: intent
  target: docs/USB_IMPORT.md
---

# Export history tracklist

## Trigger

The DJ chooses the starting recording, optional cumulative times and output file.

## Outcome

The Product reads USB history and USB track durations and saves artist/title lines beginning at the chosen entry.

## Edge cases

- Times sum full recording durations from the selected start and are estimates, not actual play timestamps.
- Cancelling the file chooser leaves the session unchanged.
