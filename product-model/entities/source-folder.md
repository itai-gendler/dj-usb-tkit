---
references:
- kind: code
  role: implementation
  target: backend/src/service/source_roots.rs
- kind: code
  role: implementation
  target: vanilla-ui/components/library/actions.mjs
- kind: spec
  role: intent
  target: docs/LIBRARY_ANALYSIS.md
---

# Source folder

A configured folder used to find library audio.

## Information kept

- **Path** — Configured directory.
- **Enabled** — Whether included in the current source selection.
- **Availability** — Whether the directory currently exists and can be used.
- **Analysis summary** — Whether its indexed tracks have core analysis.
