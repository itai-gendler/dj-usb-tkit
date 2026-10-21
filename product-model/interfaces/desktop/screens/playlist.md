---
entities:
- entity: playlist
  shows:
  - Name
  - Tracks
  - Sidebar order
  - Import source
  - Last export
  - Reorder locked
  - Track order
  collects:
  - Name
  - Tracks
  - Track order
  - Sidebar order
- entity: track
  shows:
  - Title
  - Artist
  - Album
  - File
  - Duration
  - BPM
  - Key
  - Waveform
  - Artwork
  - Genre
  - Release date
- entity: analysis-job
  shows:
  - Selection
  - Progress
  - Results
references:
- kind: code
  role: implementation
  target: vanilla-ui/index.html
---

# Playlist

Prepare one local playlist and inspect its saved order and export status.
