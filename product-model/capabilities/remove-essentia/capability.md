---
availability:
- place: desktop
references:
- kind: code
  role: implementation
  target: backend/src/tauri_commands.rs
- kind: code
  role: implementation
  target: backend/src/service/settings.rs
- kind: code
  role: implementation
  target: vanilla-ui/components/settings/events.mjs
- kind: spec
  role: intent
  target: docs/LIBRARY_ANALYSIS.md
domain: analysis
---

# Remove Essentia

Remove the installed Essentia engine files and return to the built-in Stratum engine.
