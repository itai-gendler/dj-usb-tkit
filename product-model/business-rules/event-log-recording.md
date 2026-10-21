---
appliesTo:
- type: entity
  id: event-log
- type: capability
  id: import-external-library
- type: capability
  id: export-playlist
- type: capability
  id: analyze-tracks
- type: capability
  id: diagnose-usb-device
- type: capability
  id: apply-usb-fixes
references:
- kind: code
  role: implementation
  target: vanilla-ui/components/event-log/actions.mjs#storeEventLogEntry
---

# Operations expose their warnings and outcomes in the Event Log

Import, export, analysis, diagnostics and repair messages include severity, source, time and details. The displayed log coalesces repeats; the session file keeps occurrences. Reading the log is separate from the operation that records it.
