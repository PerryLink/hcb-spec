# HCB spec

> Consumer-facing spec for the HCB compatibility/tracks model. **The canonical data lives in [dsh-compat-baseline](https://github.com/PerryLink/dsh-compat-baseline).**

## What is here

- `spec/tracks.json` — mapping of DSH-ENTRY / DSH-FLOW / DSH-BOOST into HCB fields.
- `docs/TRACKS.md` — the three tracks, evidence states, and the gate heuristic.
- `NOTICE.md` — attribution to `dsh-standards` (Apache-2.0).

## Rules

1. ENTRY / FLOW / BOOST are independent; no composite score.
2. A skip is not a pass; static is not runtime.
3. BOOST is not a gate.
4. Compatibility is declared, not tested.

## Versioning

- `hcb-tracks/1` — current mapping.
- Breaking changes require a new schema id and a migration note.
