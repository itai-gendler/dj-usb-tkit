---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ chooses the replacement directory.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::library
- text: The Product changes the source folder path and each resolved track file location.
  kind: product
  entities:
  - entity: source-folder
    effect: changes
    facts:
    - Path
    - Availability
  - entity: track
    effect: changes
    facts:
    - File
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

# Relocate all matching files

## Trigger

A configured directory has moved.

## Outcome

Matching tracks use the new directory and keep playlist membership.

## Edge cases

- The same directory, an empty destination or a nonexistent directory is rejected.
