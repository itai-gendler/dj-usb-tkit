---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ starts analysis for the selection.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::library
- text: The Product starts an analysis run for the selected recordings.
  kind: product
  entities:
  - entity: analysis-job
    effect: creates
    to: Running
    facts:
    - Selection
    - Progress
    - Results
  - entity: track
    effect: reads
    facts:
    - File
    - BPM
    - Key
    - First beat
    - Waveform
  actor: dj
  contexts:
    desktop:
      place: desktop::library
- text: The Product enriches each track while preserving eligible imported or user-edited initial values.
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
  contexts:
    desktop:
      place: desktop::library
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

# Analyze missing recordings

## Trigger

Indexed recordings need analysis.

## Outcome

The run reports completed, incomplete and failed counts and progressively refreshes recordings.

## Edge cases

- Per-recording decode failures leave remaining work running and appear in the results.
- An unavailable selected Essentia runtime produces an explicit failure, without switching to Stratum.

## Decision points

### Engine

Which engine is configured?

- Stratum → use the built-in local engine.
- Essentia → use the installed optional engine and its runtime.

### First-beat ownership

Which initial anchor is available?

- User-edited anchor → keep it on first analysis.
- Imported anchor with its retained imported BPM → keep it with that BPM.
- Neither → estimate an anchor.
