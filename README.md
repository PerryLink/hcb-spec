> **This repository is retired (2026-11-14).**
>
> HCB is now the **data/gate subproject of [dsh-standards](https://github.com/PerryLink/dsh-standards)**.
>
> - Rules, checker and ENTRY/FLOW/BOOST definitions: [dsh-standards](https://github.com/PerryLink/dsh-standards)
> - Compatibility matrix, tracks data, risk and `hcb-gate/1`: [dsh-hcb](https://github.com/PerryLink/dsh-hcb)
>
> This repo is archived for URL stability. Do not use it for new work.

# HCB spec

> Consumer-facing spec for the HCB compatibility/tracks model. **The canonical data lives in [dsh-compat-baseline](https://github.com/PerryLink/hcb).**

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
