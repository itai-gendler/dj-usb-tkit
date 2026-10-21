---
references:
- kind: code
  role: implementation
  target: backend/src/service/rekordbox_import.rs
- kind: code
  role: implementation
  target: backend/src/service/mixxx_import.rs
- kind: code
  role: implementation
  target: vanilla-ui/components/library/actions.mjs
- kind: spec
  role: intent
  target: docs/EXTERNAL_LIBRARIES.md
---

# External library

A detected rekordbox or Mixxx library on this computer.

## Information kept

- **Application** — rekordbox or Mixxx.
- **Location** — Detected database path.
- **Imported** — Whether tracks have been imported from this source.
- **Enabled** — Whether its tracks appear in the library selection.
- **Lists** — Available non-empty playlists, histories and, for Mixxx, crates.
