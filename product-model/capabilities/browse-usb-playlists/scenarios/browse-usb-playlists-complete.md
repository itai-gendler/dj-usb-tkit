---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ loads the device lists and chooses one.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::usb
- text: The Product presents USB playlist membership and USB track details, searching and sorting the complete list before
    returning a page.
  kind: product
  entities:
  - entity: usb-playlist
    effect: reads
    facts:
    - Name
    - Tracks
    - Menu order
    - Origin
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
      place: desktop::usb
references:
- kind: code
  role: implementation
  target: backend/src/service/usb.rs#fetch_usb_playlists_with_progress
- kind: code
  role: implementation
  target: backend/src/service/usb.rs#fetch_usb_playlist_tracks
- kind: spec
  role: intent
  target: docs/USB_IMPORT.md
---

# Browse USB playlists

## Trigger

The DJ loads the device lists and chooses one.

## Outcome

The Product presents USB playlist membership and USB track details, searching and sorting the complete list before returning a page.

## Edge cases

- Missing optional artwork or analysis produces warnings while usable entries remain.
- Entries whose recording cannot be found on the drive are left out.
- Lists are read from both the PDB and the eDB; neither has to be complete.
