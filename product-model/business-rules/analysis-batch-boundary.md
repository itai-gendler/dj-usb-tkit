---
appliesTo:
- type: entity
  id: analysis-job
references:
- kind: code
  role: implementation
  target: backend/src/service/analysis.rs#analyze_new_tracks_with_progress
- kind: spec
  role: intent
  target: docs/LIBRARY_ANALYSIS.md
---

# Pause and cancel take effect between recordings

In-flight work completes. Pausing prevents new work until resume; cancellation exits a pause and preserves completed results.
