---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ chooses Cancel analysis.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::library
- text: 'The Product cancels the analysis run: recordings in progress finish, no new one starts, and completed results stay.'
  kind: product
  entities:
  - entity: analysis-job
    effect: changes
    from: Running
    to: Cancelled
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

# Cancel analysis

## Trigger

The DJ chooses Cancel analysis.

## Outcome

The run is cancelled; recordings already analyzed keep their results.
