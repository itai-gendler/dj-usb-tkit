---
references:
- kind: code
  role: implementation
  target: backend/src/service/analysis.rs#analyze_new_tracks_with_progress
- kind: code
  role: implementation
  target: vanilla-ui/job_manager.mjs
- kind: spec
  role: intent
  target: docs/LIBRARY_ANALYSIS.md
---

# Analysis job

A running batch that enriches selected recordings and reports progress.

## Information kept

- **Selection** — Recordings targeted by this run.
- **Progress** — Work completed and total, with current activity.
- **Results** — Analyzed, incomplete and failed counts with warnings.

## States

### Running

The batch is processing its selection.

### Paused

Workers wait before starting another recording; in-flight work can finish.

### Completed

The batch has finished and reports results, including per-recording failures.

### Cancelled

The batch has stopped taking new work and retained completed results.
