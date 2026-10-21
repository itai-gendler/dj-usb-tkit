---
appliesTo:
- type: entity
  id: track
- type: entity
  id: external-library
- type: capability
  id: import-external-playlist
references:
- kind: code
  role: implementation
  target: backend/src/service/rekordbox_import.rs
- kind: code
  role: implementation
  target: backend/src/service/mixxx_import.rs
- kind: spec
  role: intent
  target: docs/EXTERNAL_LIBRARIES.md
---

# External imports keep local edits unless explicitly forced

Reimport updates eligible values from the same originating library, but preserves app-edited or reanalyzed values and existing cues. Force update during list import can replace BPM, key and available cues. External databases are read-only sources.
