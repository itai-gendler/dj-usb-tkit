---
kind: edge
routes:
  desktop: Desktop app
steps:
- text: The DJ requests a scan.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::library
- text: The Product reports unavailable source folders without removing indexed tracks.
  kind: product
  entities:
  - entity: source-folder
    effect: changes
    facts:
    - Availability
  - entity: track
    effect: reads
    facts: []
  actor: dj
  contexts:
    desktop:
      place: desktop::library
references:
- kind: code
  role: implementation
  target: backend/src/service/library.rs#scan_library
- kind: code
  role: implementation
  target: vanilla-ui/components/library/actions.mjs
- kind: spec
  role: intent
  target: docs/LIBRARY_ANALYSIS.md
---

# Keep indexed music when directories disappear

## Trigger

Every enabled folder is missing.

## Outcome

The app reports the unavailable folders, scans nothing and keeps every indexed recording.
