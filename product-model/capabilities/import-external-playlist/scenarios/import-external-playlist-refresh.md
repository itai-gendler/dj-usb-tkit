---
kind: alternate
routes:
  desktop: Desktop app
steps:
- text: The DJ imports the same external list again.
  kind: actor
  entities: []
  actor: dj
  contexts:
    desktop:
      place: desktop::playlist
- text: The Product replaces playlist membership using available tracks, keeps its name, and clears last export.
  kind: product
  entities:
  - entity: playlist
    effect: changes
    facts:
    - Tracks
    - Last export
    - Track order
  - entity: track
    effect: reads
    facts:
    - Sources
  actor: dj
  contexts:
    desktop:
      place: desktop::playlist
references:
- kind: code
  role: implementation
  target: backend/src/service/rekordbox_import.rs#import_rekordbox_playlist
- kind: code
  role: implementation
  target: backend/src/service/mixxx_import.rs#import_mixxx_playlist
- kind: code
  role: implementation
  target: backend/src/service/playlists.rs#save_imported_playlist
- kind: code
  role: implementation
  target: vanilla-ui/components/playlist/actions.mjs#importExternalPlaylist
- kind: spec
  role: intent
  target: docs/EXTERNAL_LIBRARIES.md
---

# Refresh a renamed imported list

## Trigger

The external list already has an associated local playlist.

## Outcome

Membership and order are replaced, the local name remains, and last export is cleared.

## Edge cases

- Deleting the local list makes the next import create it anew.
- Force update replaces BPM, key and available cues even after local edits; absent external cues do not erase local cues.
