---
scope: Core desktop music preparation, playback, USB export/import, history, diagnostics, repair and database recovery.
method: Static tracing from desktop controls through command handlers, services, stored data and selected regression examples.
covered:
- description: Desktop library, playlist, cue, playback, USB, history, backup and operation-log flows.
  paths:
  - vanilla-ui/components/
  - vanilla-ui/job_manager.mjs
  - vanilla-ui/track_utils.mjs
  - vanilla-ui/index.html
- description: Library sources, analysis, external imports, playlist preparation and native playback services.
  paths:
  - backend/src/service/library.rs
  - backend/src/service/source_roots.rs
  - backend/src/service/analysis.rs
  - backend/src/service/playlists.rs
  - backend/src/service/rekordbox_import.rs
  - backend/src/service/mixxx_import.rs
  - backend/src/service/cues.rs
  - backend/src/service/track_metadata.rs
  - backend/src/service/playback.rs
- description: USB identity, reads, initialization, export, diagnostics, repair and snapshot lifecycle services.
  paths:
  - backend/src/service/usb.rs
  - backend/src/service/usb_utils.rs
  - backend/src/service/usb_identity.rs
  - backend/src/service/export.rs
  - backend/src/service/usb_backups.rs
  - backend/src/service/engine_export.rs
  - backend/src/service/diagnostics/
  - backend/src/service/repair/
- description: Settings persistence and the desktop command integration.
  paths:
  - backend/src/service/settings.rs
  - backend/src/tauri_commands.rs
  - desktop/src-tauri/src/main.rs
exclusions:
- description: Build, release and packaging automation; development infrastructure rather than a DJ workflow.
  paths:
  - scripts/
  - .github/
  - vanilla-ui/scripts/
- description: Development probes and format-analysis binaries; no supported end-user CLI contract established.
  paths:
  - backend/src/bin/
- description: Regression harnesses and fixture data; inspection evidence rather than product abilities.
  paths:
  - backend/tests/
  - vanilla-ui/tests/
- description: Visual drawing and styling; design stays with existing frontend assets.
  paths:
  - vanilla-ui/styles.css
  - vanilla-ui/waveform.mjs
  - vanilla-ui/tooltip.mjs
unmapped:
- description: Release checking, updater installation and notification severity; peripheral lifecycle outside music preparation.
  paths:
  - backend/src/service/update_check.rs
  - vanilla-ui/update_check.mjs
- description: Theme, accent, help and donation actions in the shell; peripheral preferences and external links.
  paths:
  - vanilla-ui/components/settings/actions.mjs
  - vanilla-ui/components/settings/events.mjs
  - vanilla-ui/components/shell/
- description: Detailed binary encoding, DSP internals and individual structural repair algorithms; existing format specifications
    retain those contracts.
  paths:
  - backend/src/pdb_reader.rs
  - backend/src/edb.rs
  - backend/src/engine_db.rs
  - backend/src/service/anlz.rs
  - backend/src/service/export_helpers/
  - backend/src/service/bpm_key.rs
  - backend/src/service/repair/pdb_fixes.rs
- description: One-time legacy data transformations beyond the visible analysis edit guard; internal upgrade details.
  paths:
  - backend/src/service/migrations.rs
limitations: []
---

# Coverage


