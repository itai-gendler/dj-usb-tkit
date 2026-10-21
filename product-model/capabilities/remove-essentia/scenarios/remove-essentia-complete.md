---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ chooses Remove Essentia.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::analysis-settings
- text: The Product removes optional engine files and resets the saved engine preference in settings.
  kind: product
  entities:
  - entity: settings
    effect: changes
    facts:
    - Essentia files
    - Analysis engine
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

# Remove Essentia

## Trigger

The DJ chooses Remove Essentia.

## Outcome

The Product removes optional engine files and resets the saved engine preference in settings.
