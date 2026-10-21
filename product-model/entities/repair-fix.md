---
references:
- kind: code
  role: implementation
  target: backend/src/service/repair/run.rs
- kind: spec
  role: intent
  target: docs/DIAGNOSTICS_REPAIRS.md
---

# Repair fix

An individually selectable proposal produced by Preview Fixes.

## Information kept

- **Title** — Proposed action.
- **Description** — What will change.
- **Supported** — Whether an automatic action exists.
- **Destructive** — Whether the proposal removes or replaces content.
- **Estimated changes** — Expected writes and deletes.
- **Selection** — Chosen, required, optional, or accompanying bookkeeping.
- **Result** — Applied, skipped or failed details.

## States

### Proposed

The current preview offers the action.

### Applied

The action completed.

### Skipped

The action was not selected or had nothing left to do.

### Failed

The action reported failure.
