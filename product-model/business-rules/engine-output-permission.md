---
appliesTo:
- type: entity
  id: usb-device
  effect: changes
  facts:
  - Engine DJ library
references:
- kind: code
  role: implementation
  target: backend/src/service/engine_export.rs#engine_library_enabled
- kind: spec
  role: intent
  target: docs/ENGINE_DJ.md
permits:
- actors:
  - dj
  when:
  - entity: settings
    fact: Write Engine DJ library
    is: true
---

# The Engine DJ library is rebuilt only while Write Engine DJ library is on

The Engine DJ output is off by default. A USB change rebuilds it only when the DJ has turned on Write Engine DJ library in Export settings, or chosen the optional upkeep repair, which turns that setting on.
