---
availability:
- place: desktop
references:
- kind: code
  role: implementation
  target: backend/src/service/source_roots.rs#remove_tracks_by_source_roots
- kind: code
  role: implementation
  target: vanilla-ui/components/library/events.mjs
- kind: spec
  role: intent
  target: docs/LIBRARY_ANALYSIS.md
domain: library
---

# Remove source folder

Explicitly remove a configured source and its uncovered indexed music; removing all folders follows the same confirmation flow.
