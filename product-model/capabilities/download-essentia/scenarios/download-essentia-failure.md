---
kind: edge
routes:
  desktop: Desktop app
steps:
- text: The DJ chooses Download.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::analysis-settings
- text: The Product reports the settings installation error.
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

# Report a download failure

## Trigger

The optional engine cannot be downloaded or installed.

## Outcome

The error is visible and the DJ can retry.
