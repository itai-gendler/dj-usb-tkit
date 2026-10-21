---
kind: alternate
routes:
  desktop: Desktop app
steps:
- text: The DJ chooses Reanalyze for the selection.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::library
- text: The Product starts an analysis run for every selected recording, analyzed before or not.
  kind: product
  entities:
  - entity: analysis-job
    effect: creates
    to: Running
    facts:
    - Selection
    - Progress
    - Results
  actor: dj
  contexts: &id001
    desktop:
      place: desktop::library
- text: The Product replaces track analysis and retains cue positions.
  kind: product
  entities:
  - entity: track
    effect: changes
    facts:
    - Duration
    - BPM
    - Key
    - First beat
    - Waveform
    - Artwork
  actor: dj
  contexts:
    desktop:
      place: desktop::library
- text: The Product completes the analysis run and reports its results.
  kind: product
  entities:
  - entity: analysis-job
    effect: changes
    from: Running
    to: Completed
    facts:
    - Progress
    - Results
  actor: dj
  contexts: *id001
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

# Replace analysis while retaining cues

## Trigger

The DJ wants fresh analysis for selected recordings.

## Outcome

Fresh values replace previous waveform, BPM, key and first beat, including edited/imported values; cues remain.
