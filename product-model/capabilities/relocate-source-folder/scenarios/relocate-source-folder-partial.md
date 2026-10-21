---
kind: edge
routes:
  desktop: Desktop app
steps:
- text: The DJ supplies the replacement directory.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::library
- text: The Product changes resolved track file locations and keeps both source folder paths visible with unresolved
    counts.
  kind: product
  entities:
  - entity: track
    effect: changes
    facts:
    - File
  - entity: source-folder
    effect: changes
    facts:
    - Path
    - Availability
  actor: dj
  contexts:
    desktop:
      place: desktop::library
references:
- kind: code
  role: implementation
  target: backend/src/service/source_roots.rs#relocate_source_root
- kind: code
  role: implementation
  target: vanilla-ui/components/library/actions.mjs#relocateSourceRoot
- kind: spec
  role: intent
  target: docs/LIBRARY_ANALYSIS.md
---

# Retain unresolved files during relocation

## Trigger

Some relative file paths are missing or already indexed at the destination.

## Outcome

Resolved tracks move; unresolved tracks remain associated with the old visible source for follow-up.
