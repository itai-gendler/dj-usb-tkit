---
appliesTo:
- type: entity
  id: settings
  effect: changes
  facts:
  - Analysis engine
  - BPM range
  - Sync mode
  - Write Engine DJ library
  - Backup before export
  - Backup retention
  - Key notation
permits:
- actors:
  - dj
references:
- kind: code
  role: implementation
  target: vanilla-ui/components/settings/events.mjs#bindSettingsEvents
---

# The DJ changes the app's settings

The app has no accounts or roles: whoever uses it on this computer chooses its analysis, export, backup and key-notation settings.
