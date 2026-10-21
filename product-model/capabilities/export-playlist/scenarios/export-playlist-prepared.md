---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: The DJ chooses Export for the prepared list.
  kind: actor
  entities: []
  actor: dj
  contexts: &id001
    desktop:
      place: desktop::playlist
- text: The Product saves a column sort still showing on the list as its saved order.
  kind: product
  entities:
  - entity: playlist
    effect: changes
    facts:
    - Track order
  actor: dj
  contexts: *id001
- text: Every recording already has its waveform, BPM, duration and analysis files, and no source folder it comes from is
    missing.
  kind: condition
  entities:
  - entity: track
    effect: reads
    facts:
    - Duration
    - BPM
    - Waveform
    - Sources
  - entity: source-folder
    effect: reads
    facts:
    - Availability
  actor: dj
  contexts: *id001
- text: The selected drive is writable and has room for the new copies plus reserved headroom.
  kind: condition
  entities:
  - entity: usb-device
    effect: reads
    facts:
    - Writable
  actor: dj
  contexts: *id001
- text: The Product reads the sync mode, and whether to snapshot the databases first, from settings.
  kind: product
  entities:
  - entity: settings
    effect: reads
    facts:
    - Sync mode
    - Backup before export
  actor: dj
  contexts: *id001
- text: The Product copies each recording the drive lacks, with its analysis files and artwork, and applies saved cue and
    grid edits to the copied analysis.
  kind: product
  entities:
  - entity: track
    effect: reads
    facts:
    - File
    - BPM
    - First beat
    - Artwork
    - Hot cues
    - Memory cues
    - Playback start
  - entity: usb-track
    effect: creates
    facts:
    - Title
    - Artist
    - Album
    - Media
    - Duration
    - BPM
    - Key
    - First beat
    - Waveform
    - Artwork
    - Hot cues
    - Memory cues
    - Playback start
    - Genre
    - Rating
    - Release date
    - Local match
  actor: dj
  contexts: *id001
- text: The Product writes the membership and order of the same-name USB playlist for the sync mode and moves it to the top
    of the drive's lists.
  kind: product
  entities:
  - entity: usb-playlist
    effect: changes
    facts:
    - Tracks
    - Menu order
  actor: dj
  contexts: *id001
- text: The Product records the export time, drive and count as the playlist's last export.
  kind: product
  entities:
  - entity: playlist
    effect: changes
    facts:
    - Last export
  actor: dj
  contexts: *id001
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

# Export prepared music

## Trigger

The DJ has a prepared playlist and a writable drive selected.

## Outcome

The drive's playlist with the same name matches the app playlist as the sync mode says and sits first among the drive's lists; the app playlist shows when, to which drive and how many recordings it was exported.

## Edge cases

- Key and artwork are not required; a recording without them still exports.
- Export copies the existing analysis rather than analyzing the audio again.
- Compatible extensible WAV headers are normalized without changing sample data.

## Decision points

### Sync mode

Which sync mode is set?

- Mirror (default) → the drive's list takes the app playlist's membership and order; export-owned files no other playlist or play history uses are removed.
- Additive → the drive's list keeps its membership and order and gains only the missing recordings; nothing is removed.

### Database backup

Is Backup before export on?

- On (default) → existing PDB and eDB files are snapshotted before the database writes.
- Off → export takes no snapshot of its own.

### Target list

Does the drive already have a playlist with this name?

- Yes → that list is updated by the sync mode.
- No → a new list with this name is created.
