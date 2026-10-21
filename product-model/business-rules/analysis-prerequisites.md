---
appliesTo:
- type: entity
  id: track
- type: capability
  id: export-playlist
references:
- kind: code
  role: implementation
  target: backend/src/service/export.rs#ensure_playlist_tracks_analysis_ready
- kind: spec
  role: intent
  target: docs/USB_EXPORT.md
---

# Export needs every recording analyzed first

Required waveform, BPM, duration and DAT/EXT files precede export. A key or cover is optional. Export copies analysis and applies saved cue/grid edits; it does not perform the missing audio analysis itself.
