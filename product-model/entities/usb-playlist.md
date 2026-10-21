---
relations:
- entity: usb-track
  verb: includes
  cardinality: many-to-many
references:
- kind: code
  role: implementation
  target: backend/src/service/usb.rs#fetch_usb_playlists_with_progress
- kind: spec
  role: intent
  target: docs/USB_IMPORT.md
---

# USB playlist

A playlist read from the selected drive, with its device membership and order.

## Information kept

- **Name** — Device playlist name, including folder context when displayed.
- **Tracks** — Ordered USB recordings.
- **Menu order** — Position among sibling playlists.
- **Origin** — Which device database supplied the list.
