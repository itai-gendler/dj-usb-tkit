---
appliesTo:
- type: entity
  id: source-folder
- type: capability
  id: scan-library
- type: capability
  id: export-playlist
- type: capability
  id: relocate-source-folder
references:
- kind: code
  role: implementation
  target: backend/src/service/library.rs#scan_library
- kind: code
  role: implementation
  target: backend/src/service/source_roots.rs#export_blocking_missing_source_roots
- kind: spec
  role: intent
  target: docs/LIBRARY_ANALYSIS.md
---

# Missing source folders preserve indexed music

A missing configured directory is recoverable state. Scans prune only available roots, relocation preserves recording identity, and export refuses a selected list depending on a missing configured root.
