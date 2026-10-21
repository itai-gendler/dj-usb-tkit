---
appliesTo:
- type: entity
  id: analysis-job
- type: capability
  id: analyze-tracks
- type: capability-scenario
  id: edit-beat-grid-local
- type: capability-scenario
  id: add-cue-local
- type: capability-scenario
  id: edit-cue-local
- type: capability-scenario
  id: remove-cue-local
- type: capability-scenario
  id: change-playback-start-local
- type: capability-scenario
  id: edit-track-metadata-local
references:
- kind: code
  role: implementation
  target: backend/src/service/migrations.rs#ensure_no_data_migration
- kind: spec
  role: intent
  target: docs/APP_DATA_MODEL.md
- kind: code
  role: implementation
  target: backend/src/service/track_metadata.rs#save_track_metadata_edits
---

# Analysis and local analysis edits wait for a background data upgrade

New analysis and local analysis and metadata saves wait while a background upgrade owns the cached analysis.
