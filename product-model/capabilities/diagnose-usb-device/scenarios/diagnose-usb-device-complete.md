---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ chooses Rediagnose USB.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::usb
- text: The Product presents USB device diagnostics for database structure, content and analysis references, list
    resolution, menus and optional Engine DJ output.
  kind: product
  entities:
  - entity: usb-device
    effect: changes
    facts:
    - Diagnostics
  actor: dj
  contexts:
    desktop:
      place: desktop::usb
references:
- kind: code
  role: implementation
  target: backend/src/service/diagnostics/run.rs#run_usb_diagnostics_with_progress
- kind: spec
  role: intent
  target: docs/DIAGNOSTICS_REPAIRS.md
---

# Diagnose USB device

## Trigger

The DJ chooses Rediagnose USB.

## Outcome

The Product presents USB device diagnostics for databases, content references, analysis references, playlists, menus and optional Engine DJ output.

## Edge cases

- Operational checks emphasize database references and do not scan every analysis file.
- Findings can link to details in the Event Log.
