---
references:
- kind: code
  role: implementation
  target: vanilla-ui/components/usb/actions.mjs
---

# USB Browser

USB Browser: the selected drive, its playlists and player menu, its health and its repairs.

## Boundary

Owns choosing, naming and initializing a drive, its playlists and player menu, diagnostics, parity and repairs. Does not own local music folders, or exporting an app playlist, which starts from the playlist.
