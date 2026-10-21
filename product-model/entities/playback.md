---
references:
- kind: code
  role: implementation
  target: backend/src/service/playback.rs
- kind: code
  role: implementation
  target: backend/src/player.rs
- kind: spec
  role: intent
  target: docs/PLAYLISTS_PLAYBACK.md
---

# Playback

The current native listening session.

## Information kept

- **Recording** — The selected recording.
- **Source** — Library or USB audio actually used.
- **Position** — Current offset.
- **Metronome** — Enabled state, beat grid and music/click balance.

## States

### Stopped

No recording is playing.

### Playing

The loaded recording advances audibly.

### Paused

The loaded recording is held at its current position.
