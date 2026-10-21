---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ chooses Pause analysis.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::library
- text: 'The Product pauses the analysis run: recordings already in progress finish, and no new one starts.'
  kind: product
  entities:
  - entity: analysis-job
    effect: changes
    from: Running
    to: Paused
    facts:
    - Progress
    - Results
  actor: dj
  contexts:
    desktop:
      place: desktop::library
references:
- kind: code
  role: implementation
  target: backend/src/service/analysis.rs
- kind: spec
  role: intent
  target: docs/LIBRARY_ANALYSIS.md
---

# Pause analysis

## Trigger

The DJ chooses Pause analysis.

## Outcome

The run is paused: in-flight recordings finish and no new recording starts until it is resumed.
