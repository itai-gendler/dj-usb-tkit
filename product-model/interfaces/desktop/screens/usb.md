---
entities:
- entity: usb-device
  shows:
  - Root
  - Name
  - Writable
  - Structure
  - Last seen
  - Database contents
  - Engine DJ library
  - Diagnostics
  - Parity
  collects:
  - Root
  - Name
- entity: usb-playlist
  shows:
  - Name
  - Tracks
  - Menu order
  - Origin
  collects:
  - Menu order
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
- entity: repair-fix
  shows:
  - Title
  - Description
  - Supported
  - Destructive
  - Estimated changes
  - Selection
  - Result
  collects:
  - Selection
references:
- kind: code
  role: implementation
  target: vanilla-ui/index.html
---

# USB Browser

Inspect the selected drive, its playlists, operational health, parity and repair proposals. These are views of the same selected device.
