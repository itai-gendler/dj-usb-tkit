---
appliesTo:
- type: entity
  id: playlist
- type: capability
  id: export-playlist
references:
- kind: code
  role: implementation
  target: backend/src/service/export.rs#run_manifest_invariant_check
---

# Mirror export requires a complete exportable selection

If source checks skip any selected recording, mirror export stops before database membership writes and pruning. Additive may append an available subset, with warnings; an entirely empty export is rejected.
