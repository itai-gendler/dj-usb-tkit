---
kind: validation
routes:
  desktop: Desktop app
steps:
- text: The DJ requests Export.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::playlist
- text: The Product reads mirror settings and checks track source files.
  kind: product
  entities:
  - entity: settings
    effect: reads
    facts:
    - Sync mode
  - entity: track
    effect: reads
    facts:
    - File
  actor: dj
  contexts:
    desktop:
      place: desktop::playlist
- text: The Product reports that skipped recordings prevent mirror export.
  kind: product
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::playlist
references:
- kind: code
  role: implementation
  target: backend/src/service/export.rs#export_to_usb_with_progress
- kind: code
  role: implementation
  target: backend/src/service/export.rs#run_manifest_invariant_check
- kind: code
  role: implementation
  target: vanilla-ui/components/usb/actions.mjs#exportPlaylistToUsb
- kind: spec
  role: intent
  target: docs/USB_EXPORT.md
---

# Refuse incomplete mirror membership

## Trigger

Individual source files have disappeared while required analysis is still present.

## Outcome

Mirror export stops before database membership writes and pruning when any recording was skipped.
