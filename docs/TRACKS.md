# Three tracks, one compatibility overlay

HCB follows the DSH-ENTRY / DSH-FLOW / DSH-BOOST model from [dsh-standards](https://github.com/PerryLink/dsh-standards). **They are three tracks, not three levels.**

| Track | Question | Gates | Evidence states | HCB column |
|---|---|---|---|---|
| **DSH-ENTRY** | can it be recognized, installed, booted? | G0–G5 | runtime / recognized / static / blocked / failed / not-run / stale | `standards.entry` |
| **DSH-FLOW** | can a user install, configure, use, recover, uninstall? | J1–J8 | runtime / manual / not-run / failed / stale | `standards.flow` |
| **DSH-BOOST** | does it use Cordis natively and efficiently? | LEV-1–8 | measured / not-measured / failed / stale | `standards.boost` |

## Rules HCB enforces

1. **No total score.** HCB never adds ENTRY + FLOW + BOOST into a number.
2. **No skip-as-pass.** Missing declaration = `unknown`; a declared `not-run` stays `not-run`.
3. **BOOST is not a gate.** A measured BOOST never upgrades a failed ENTRY or FLOW.
4. **Compatibility is separate.** `declared-compatible` is a claim by the package author, not a test result.

## What HCB adds

- **Compatibility overlay**: does the declared `engines.dsh` range cover the latest host?
- **Risk overlay**: what capability surface does the plugin request (`subprocess`, `network:egress`, `fs:read`, ...)?
- **Gate heuristic** (`hcb-gate/1`): a *review* recommendation, not a certification:

| Decision | When |
|---|---|
| `blocked` | declared range excludes latest host, or ENTRY is `failed`/`blocked` |
| `review` | no declared range, or ENTRY is `not-run`/`unknown`/`stale`, or risk is `high`/`unknown` |
| `pilot` | compatible, but FLOW is not runtime/manual or ENTRY is not runtime |
| `production-candidate` | compatible + ENTRY runtime + FLOW runtime/manual + risk low/medium |

**Gate is not quality.** A `production-candidate` can still be a bad plugin; it only means the checks HCB knows about did not find a blocker.

## Source of truth

- Canonical model: `dsh-standards/spec/levels.json` (Apache-2.0).
- HCB mapping: `spec/tracks.json`.
- HCB does not relicense the model; see `NOTICE.md`.
