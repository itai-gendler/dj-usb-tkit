---
entities:
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
  - Sources
  - Genre
  - Release date
- entity: source-folder
  shows:
  - Path
  - Enabled
  - Availability
  - Analysis summary
  collects:
  - Path
  - Enabled
- entity: external-library
  shows:
  - Application
  - Location
  - Imported
  - Enabled
  collects:
  - Enabled
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

# Media Library

Browse configured music sources and indexed recordings.
