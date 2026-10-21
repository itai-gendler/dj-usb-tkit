---
kind: alternate
routes:
  desktop: Desktop app
steps:
- text: The DJ chooses Cancel.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::library
- text: The Product cancels the paused analysis run at once, without resuming it first, and keeps its completed results.
  kind: product
  entities:
  - entity: analysis-job
    effect: changes
    from: Paused
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

# Cancel paused work

## Trigger

An analysis batch is paused.

## Outcome

Cancellation exits the paused wait and preserves completed work.
