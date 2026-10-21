---
references:
- kind: code
  role: implementation
  target: vanilla-ui/components/settings/events.mjs
---

# Analysis

The Analysis section of Settings: the analysis engine, the BPM range and the optional Essentia engine files.

## Boundary

Owns analysis preferences and downloading, cancelling and removing Essentia. Does not own running analysis, which starts from the library and playlists.
