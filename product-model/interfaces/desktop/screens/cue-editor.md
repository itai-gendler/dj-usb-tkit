---
entities:
- entity: track
  shows:
  - Title
  - Artist
  - Album
  - Duration
  - BPM
  - Key
  - First beat
  - Waveform
  - Hot cues
  - Memory cues
  - Playback start
  - Genre
  - Rating
  - Release date
  collects:
  - BPM
  - Key
  - First beat
  - Hot cues
  - Memory cues
  - Playback start
  - Genre
  - Rating
  - Release date
- entity: usb-track
  shows:
  - Title
  - Artist
  - Album
  - Duration
  - BPM
  - Key
  - First beat
  - Waveform
  - Hot cues
  - Memory cues
  - Playback start
  - Genre
  - Rating
  - Release date
  collects:
  - BPM
  - Key
  - First beat
  - Hot cues
  - Memory cues
  - Playback start
  - Genre
  - Rating
  - Release date
- entity: playback
  shows:
  - Recording
  - Source
  - Position
  - Metronome
  collects:
  - Position
  - Metronome
references:
- kind: code
  role: implementation
  target: vanilla-ui/index.html
---

# Cue Editor

Inspect and edit one recording, its cues, beat grid and playback start.
