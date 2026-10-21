---
id: dj-usb-tkit
summary: Local-first DJ library preparation, native playback and USB export with diagnostics and recovery.
category: music
tags:
- dj
- music-library
- usb-export
authors:
- name: DJ USB Tkit contributors
license: AGPL-3.0-or-later
languages:
- en
limitations:
- Indexing, playlists, USB import and export, diagnostics, repairs and playback run locally, with no cloud account.
- rekordbox and Mixxx libraries on this computer are read-only import sources.
- A recording has at most eight hot cues, lettered A–H in time order.
- Partitioning and formatting a drive happen outside the app; the app initializes the player folders and databases on an existing
  writable drive.
- Database backups hold the PDB and eDB files only; audio backups are the user's own.
references:
- kind: code
  role: implementation
  target: desktop/src-tauri/src/main.rs
- kind: code
  role: implementation
  target: vanilla-ui/index.html
- kind: spec
  role: intent
  target: README.md
---

# DJ USB Tkit

DJ USB Tkit is a local-first DJ library manager. It scans and analyzes music, prepares playlists and cues, plays audio, and exports playlists to USB drives for players that read rekordbox or Engine DJ libraries. Diagnostics, preview-first repairs and database backups help keep those drives working.

## Intent

- Local-first desktop workflows: no cloud dependency for indexing, playlists, USB import/export, diagnostics/repairs, or playback.
- A fast prep flow: index the library quickly, build playlists, analyze only the missing tracks for the target playlist, then export.
- Strict parity reporting is kept separate from operational passability, so users can tell "works" from "fully parity-clean".
- A pluggable analysis engine: Stratum by default, Essentia as an option.

## Documentation relationship

This model complements the project\'s existing [documentation](../docs/README.md). The [App Data Model](../docs/APP_DATA_MODEL.md), [USB Export](../docs/USB_EXPORT.md), [PDB](../docs/PDB.md) and [eDB](../docs/eDB.md) references remain the authority for data fields and file formats; the model links to them rather than repeating them.
