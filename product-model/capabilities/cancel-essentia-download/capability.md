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

# Cancel Essentia download

Stop a running download of the Essentia engine files.
