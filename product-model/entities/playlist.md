---
relations:
- entity: track
  verb: includes
  cardinality: many-to-many
references:
- kind: code
  role: implementation
  target: backend/src/service/playlists.rs
- kind: code
  role: implementation
  target: backend/src/service/export.rs#compute_playlist_usb_export_status
- kind: spec
  role: intent
  target: docs/PLAYLISTS_PLAYBACK.md
---

# Playlist

A local preparation list with ordered track membership.

## Information kept

- **Name** — User-editable name.
- **Tracks** — Distinct library recordings in the list.
- **Track order** — Saved order of the list's recordings.
- **Sidebar order** — Local list position.
- **Import source** — External list associated with this playlist, when imported.
- **Last export** — Most recent export time, drive and count, cleared when relevant content changes.
- **Reorder locked** — Whether additive export to an existing same-name USB playlist locks local ordering.
