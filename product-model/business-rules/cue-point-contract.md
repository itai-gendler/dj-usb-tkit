---
appliesTo:
- type: entity
  id: track
- type: entity
  id: usb-track
references:
- kind: code
  role: implementation
  target: backend/src/service/cues.rs#split_cues
- kind: code
  role: implementation
  target: backend/src/service/cues.rs#anlz_cues_from_track_cues
- kind: spec
  role: intent
  target: docs/CUE_EDITOR.md
---

# Hot cues use eight time-ordered pads and memory cues use none

Hot cues are at most eight, with position-based A–H assignment. Each exports as a memory point and a hot-cue pad. Memory cues are memory-only, may be uncoloured and do not consume pads; positions are distinct from other cues. The optional playback start has no pad and cannot follow the first hot cue.
