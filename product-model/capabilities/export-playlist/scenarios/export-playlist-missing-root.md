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
- text: The Product reports the missing source folder affecting playlist membership.
  kind: product
  entities:
  - entity: source-folder
    effect: reads
    facts:
    - Path
    - Enabled
    - Availability
    - Analysis summary
  - entity: playlist
    effect: reads
    facts:
    - Name
    - Tracks
    - Sidebar order
    - Import source
    - Last export
    - Reorder locked
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

# Protect a playlist whose source folder disappeared

## Trigger

A selected recording belongs to a configured missing directory.

## Outcome

Export is blocked until the directory is relocated or explicitly removed.
