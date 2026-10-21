---
references:
- kind: code
  role: implementation
  target: backend/src/service/usb_backups.rs
- kind: spec
  role: intent
  target: docs/USB_EXPORT.md
---

# Backup

A timestamped snapshot of the PDB and eDB files that existed at the time.

## Information kept

- **Timestamp** — When the snapshot was taken.
- **Files** — PDB, eDB, or both, and their combined size.
- **Location** — On USB or on this computer.
- **Reason** — Operation that triggered the snapshot, when recorded.
- **Playlist count** — Count recorded at backup time when known.
