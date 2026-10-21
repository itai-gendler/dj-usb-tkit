---
kind: edge
routes:
  desktop: Desktop app
steps:
- text: The DJ requests analysis.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::library
- text: The Product reads settings and reports unavailable engine setup.
  kind: product
  entities:
  - entity: settings
    effect: reads
    facts:
    - Analysis engine
    - Essentia files
  actor: dj
  contexts:
    desktop:
      place: desktop::library
references:
- kind: code
  role: implementation
  target: backend/src/service/analysis.rs#analyze_new_tracks_with_progress
- kind: code
  role: implementation
  target: backend/src/service/analysis.rs#kept_analysis_values
- kind: spec
  role: intent
  target: docs/LIBRARY_ANALYSIS.md
---

# Report unavailable analysis engine

## Trigger

Essentia is selected but cannot be started.

## Outcome

The run reports the runtime error and does not silently change engines.
