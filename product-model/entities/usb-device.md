---
relations:
- entity: usb-playlist
  verb: holds
  cardinality: one-to-many
- entity: usb-track
  verb: stores
  cardinality: one-to-many
- entity: usb-history
  verb: carries
  cardinality: one-to-many
- entity: backup
  verb: has
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: backend/src/service/usb.rs#validate_usb_root
- kind: code
  role: implementation
  target: backend/src/service/usb.rs#set_usb_device_name
- kind: code
  role: implementation
  target: backend/src/service/engine_export.rs
- kind: spec
  role: intent
  target: docs/USB_EXPORT.md
---

# USB device

A selected or remembered USB root and its user-assigned identity.

## Information kept

- **Root** — Current folder used to access the drive.
- **Name** — Portable user-assigned name, if set.
- **Writable** — Whether writes are available at the selected root.
- **Structure** — Presence of Contents, PIONEER, PDB and eDB.
- **Listed** — Whether this root appears among remembered devices.
- **Last seen** — Remembered connection information.
- **Database contents** — The player-visible library and its metadata.
- **Engine DJ library** — Presence and synchronization state of the optional Engine DJ output.
- **Diagnostics** — Operational checks and warnings for the selected drive.
- **Parity** — Strict comparison of PDB and eDB.
