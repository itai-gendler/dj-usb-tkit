---
relations:
- entity: usb-track
  verb: contains
  cardinality: many-to-many
references:
- kind: code
  role: implementation
  target: backend/src/service/usb.rs#fetch_usb_histories_with_progress
- kind: spec
  role: intent
  target: docs/USB_IMPORT.md
---

# USB history

A device play session read from the selected USB.

## Information kept

- **Name** — Session name.
- **Date** — Recorded date or the best available estimate.
- **Tracks** — Recordings in session play order.
- **Count** — Number of resolved entries.
