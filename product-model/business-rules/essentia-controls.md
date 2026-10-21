---
appliesTo:
- type: entity
  id: settings
  effect: changes
  facts:
  - Essentia files
permits:
- actors:
  - dj
  when:
  - fact: Analysis engine
    is: essentia
references:
- kind: code
  role: implementation
  target: vanilla-ui/components/settings/events.mjs#renderEssentiaInstallRow
---

# Essentia files are downloaded or removed only while Essentia is the selected engine

The download, cancel and remove controls appear in Analysis settings once Essentia is chosen as the engine, next to whether its runtime is available.
