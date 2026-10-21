---
references:
- kind: code
  role: implementation
  target: vanilla-ui/components/backups/actions.mjs
---

# Backups

The Backups panel of the USB Browser: the database snapshots kept for the selected drive.

## Boundary

Owns browsing, restoring and deleting database snapshots. Does not own the backup preferences in Settings or any backup of audio files.
