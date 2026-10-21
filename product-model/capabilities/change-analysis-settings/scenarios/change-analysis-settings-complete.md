---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ chooses the analysis engine and BPM range.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::analysis-settings
- text: The Product saves the engine and BPM range in settings for later analysis runs.
  kind: product
  entities:
  - entity: settings
    effect: changes
    facts:
    - Analysis engine
    - BPM range
  actor: dj
  contexts:
    desktop:
      place: desktop::analysis-settings
references:
- kind: code
  role: implementation
  target: vanilla-ui/components/settings/events.mjs
- kind: code
  role: implementation
  target: backend/src/service/settings.rs#set_frontend_setting
- kind: spec
  role: intent
  target: docs/APP_DATA_MODEL.md
---

# Change Analysis settings

## Trigger

The DJ chooses the desired preference values.

## Outcome

Later analysis runs use the chosen engine and BPM range; recordings already analyzed keep their values until they are reanalyzed.
