---
availability:
- place: desktop
references:
- kind: code
  role: implementation
  target: backend/src/service/rekordbox_import.rs#scan_rekordbox_db
- kind: code
  role: implementation
  target: backend/src/service/mixxx_import.rs#scan_mixxx_db
- kind: spec
  role: intent
  target: docs/EXTERNAL_LIBRARIES.md
domain: library
---

# Import external library

Read a detected rekordbox or Mixxx database into the local music collection.
