---
singleton: true
references:
- kind: code
  role: implementation
  target: backend/src/service/settings.rs
- kind: code
  role: implementation
  target: vanilla-ui/components/settings/events.mjs
- kind: code
  role: implementation
  target: backend/src/service/migrations.rs
- kind: spec
  role: intent
  target: docs/APP_DATA_MODEL.md
---

# Settings

Preferences kept for this app installation.

## Information kept

- **Analysis engine** — Stratum by default, or optional Essentia.
- **BPM range** — Range used by subsequent analysis.
- **Sync mode** — Mirror by default, or additive.
- **Write Engine DJ library** — Off by default; enables rebuilding the Engine DJ output after USB changes.
- **Backup before export** — On by default.
- **Backup retention** — Snapshots retained per database file, default ten.
- **Key notation** — Classic or Camelot display.
- **Essentia files** — Installation or download status and runtime availability.
