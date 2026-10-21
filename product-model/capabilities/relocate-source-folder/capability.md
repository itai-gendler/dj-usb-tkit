---
availability:
- place: desktop
references:
- kind: code
  role: implementation
  target: backend/src/service/source_roots.rs#relocate_source_root
- kind: code
  role: implementation
  target: vanilla-ui/components/library/actions.mjs#relocateSourceRoot
- kind: spec
  role: intent
  target: docs/LIBRARY_ANALYSIS.md
domain: library
---

# Relocate source folder

Reconnect indexed recordings to a moved directory while preserving their identity and playlist membership.
