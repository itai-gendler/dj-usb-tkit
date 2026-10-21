---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ chooses Cancel Essentia download.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::analysis-settings
- text: The Product requests download cancellation and reports settings installation status.
  kind: product
  entities:
  - entity: settings
    effect: changes
    facts:
    - Essentia files
  actor: dj
  contexts:
    desktop:
      place: desktop::analysis-settings
references:
- kind: code
  role: implementation
  target: backend/src/tauri_commands.rs
- kind: code
  role: implementation
  target: backend/src/service/settings.rs
- kind: code
  role: implementation
  target: vanilla-ui/components/settings/events.mjs
- kind: spec
  role: intent
  target: docs/LIBRARY_ANALYSIS.md
---

# Cancel Essentia download

## Trigger

The DJ chooses Cancel Essentia download.

## Outcome

The Product requests download cancellation and reports settings installation status.
