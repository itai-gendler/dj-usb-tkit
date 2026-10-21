---
availability:
- place: desktop
references:
- kind: code
  role: implementation
  target: backend/src/service/library.rs#scan_library
- kind: code
  role: implementation
  target: vanilla-ui/components/library/actions.mjs
- kind: spec
  role: intent
  target: docs/LIBRARY_ANALYSIS.md
domain: library
---

# Scan library

Index music under enabled folders, then automatically analyze missing eligible recordings in the current library selection.
