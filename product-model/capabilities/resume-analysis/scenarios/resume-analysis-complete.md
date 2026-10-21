---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ chooses Resume analysis.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::library
- text: The Product resumes the analysis run, which takes the remaining recordings again.
  kind: product
  entities:
  - entity: analysis-job
    effect: changes
    from: Paused
    to: Running
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

# Resume analysis

## Trigger

The DJ chooses Resume analysis.

## Outcome

The run continues with the remaining recordings.
