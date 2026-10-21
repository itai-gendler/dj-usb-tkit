---
references:
- kind: code
  role: implementation
  target: backend/src/service/library.rs#row_to_track
- kind: code
  role: implementation
  target: backend/src/service/cues.rs#get_track_detail
- kind: code
  role: implementation
  target: backend/src/service/track_metadata.rs#library_metadata
- kind: spec
  role: intent
  target: docs/APP_DATA_MODEL.md
---

# Track

An indexed library recording, including music imported from a folder, rekordbox, Mixxx, or a USB.

## Information kept

- **Title** — Track name.
- **Artist** — Performing artist.
- **Album** — Album when known.
- **File** — Source audio location and format.
- **Duration** — Known playing time.
- **BPM** — Tempo and whether it came from analysis, an import, or an edit.
- **Key** — Musical key and its source.
- **First beat** — Beat-grid anchor and its source.
- **Waveform** — Preview and availability of the analysis bundle.
- **Artwork** — Available cover image.
- **Sources** — Folder and external-library origins.
- **Hot cues** — Up to eight named, coloured positions, ordered in time.
- **Memory cues** — Named, optionally coloured memory positions.
- **Playback start** — Optional memory-only start position.
- **Genre** — Genre and whether it was edited here.
- **Rating** — Zero to five stars.
- **Release date** — Full or partial release date and its source.
