---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ chooses Download Essentia.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::analysis-settings
- text: The Product downloads the optional engine files and reports installation progress in settings.
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

# Download Essentia

## Trigger

The DJ chooses Download Essentia.

## Outcome

The Product downloads the optional engine files and reports installation progress in settings.
