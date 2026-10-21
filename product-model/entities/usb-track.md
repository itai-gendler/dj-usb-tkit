---
relations:
- entity: track
  verb: matches
  cardinality: many-to-many
references:
- kind: code
  role: implementation
  target: backend/src/service/usb.rs#inspect_usb_track
- kind: code
  role: implementation
  target: backend/src/service/cues.rs#get_usb_track_detail
- kind: code
  role: implementation
  target: backend/src/service/track_metadata.rs#usb_metadata
- kind: spec
  role: intent
  target: docs/USB_IMPORT.md
---

# USB track

A recording on a drive, which may match an indexed local recording.

## Information kept

- **Title** — Track name.
- **Artist** — Artist name.
- **Album** — Album when known.
- **Media** — Device media path and format.
- **Duration** — Known playing time.
- **BPM** — Device tempo.
- **Key** — Device musical key.
- **First beat** — Device beat-grid anchor.
- **Waveform** — Available device analysis and preview.
- **Artwork** — Device cover image.
- **Hot cues** — Named and coloured hot-cue positions.
- **Memory cues** — Memory-only positions and labels.
- **Playback start** — Optional start marker.
- **Genre** — Device genre.
- **Rating** — Device star rating.
- **Release date** — Full date stored on the device.
- **Local match** — Matching library recording when resolved.
