---
availability:
- place: desktop
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

# Analyze tracks

Generate waveform, artwork, duration, BPM, key and beat-grid information for a selection; Reanalyze explicitly replaces detected or edited analysis values.
