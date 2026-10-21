---
appliesTo:
- type: entity
  id: usb-history
references:
- kind: code
  role: implementation
  target: backend/src/service/usb.rs#apply_history_dates_from_track_date_created
- kind: code
  role: implementation
  target: vanilla-ui/track_utils.mjs#buildTracklistText
- kind: spec
  role: intent
  target: docs/USB_IMPORT.md
---

# History tracklist times are cumulative duration estimates

Tracklist time offsets sum known durations starting at the chosen entry. Session dates can come from hardware or estimates. Neither establishes an actual per-recording play timestamp.
