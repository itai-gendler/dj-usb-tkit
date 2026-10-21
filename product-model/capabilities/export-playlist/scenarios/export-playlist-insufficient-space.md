---
kind: validation
routes:
  desktop: Desktop app
steps:
- text: The DJ requests Export.
  kind: actor
  actor: dj
  entities: []
  contexts:
    desktop:
      place: desktop::playlist
- text: The Product reports insufficient USB device space for the prepared playlist.
  kind: product
  actor: dj
  entities:
  - entity: usb-device
    effect: reads
    facts: []
  - entity: playlist
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::playlist
references:
- kind: code
  role: implementation
  target: backend/src/service/export.rs#ensure_usb_has_space_for_export
---

# Refuse export without sufficient free space

## Trigger

The drive has less free space than estimated new copies plus reserved headroom.

## Outcome

Export reports estimated required and available space before media copy.
