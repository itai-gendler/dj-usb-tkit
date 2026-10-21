---
entities:
- entity: usb-device
  shows:
  - Name
  - Root
- entity: usb-history
  shows:
  - Name
  - Date
  - Tracks
  - Count
- entity: usb-track
  shows:
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
references:
- kind: code
  role: implementation
  target: vanilla-ui/index.html
---

# USB History

Browse play sessions and their recordings on the selected drive.
