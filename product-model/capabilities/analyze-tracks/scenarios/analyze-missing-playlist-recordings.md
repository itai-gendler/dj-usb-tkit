---
kind: alternate
routes:
  desktop: Desktop app
steps:
- text: The DJ requests analysis for missing recordings in the current list.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::playlist
- text: The Product starts an analysis run for the recordings that need it.
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
      place: desktop::playlist
- text: The Product reads playlist membership and enriches unready tracks.
  kind: product
  entities:
  - entity: playlist
    effect: reads
    facts:
    - Name
    - Tracks
    - Sidebar order
    - Import source
    - Last export
    - Reorder locked
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
      place: desktop::playlist
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

# Analyze missing playlist recordings

## Trigger

The open list reports recordings lacking required analysis.

## Outcome

Analysis targets the entire matching playlist selection, including unready USB-rooted library rows.
