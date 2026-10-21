---
type: desktop-app
actors:
- dj
languages:
- en
references:
- kind: code
  role: implementation
  target: desktop/src-tauri/src/main.rs
- kind: code
  role: implementation
  target: vanilla-ui/index.html
- kind: spec
  role: intent
  target: README.md
---

# Desktop app

The local desktop application used to prepare music and connected drives. Its library, playlist, USB, history, backup and settings workflows share one DJ audience. Core workflows require no product sign-in.
