---
appliesTo:
- type: entity
  id: track
references:
- kind: code
  role: implementation
  target: backend/src/service/analysis.rs#kept_analysis_values
- kind: spec
  role: intent
  target: docs/LIBRARY_ANALYSIS.md
---

# First analysis keeps edited and imported values; Reanalyze replaces them

First analysis keeps user/import-owned BPM and key; it keeps an edited first beat or an imported first beat paired with retained imported BPM. Reanalysis replaces those values but retains cues.
