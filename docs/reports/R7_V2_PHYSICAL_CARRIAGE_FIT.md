# R7 V2 scoped physical carriage-fit report

Recorded 2026-09-04 from the owner's direct report. No new photograph, measurement or physical inspection by the agent is claimed.

## Article and scope

`R7_ARCHITECTURE_V2_Candidate_001` has been printed. The Ender donor was NEVER disassembled: original X-axis hardware remains assembled/in place. The print seats on the real Ender carriage and visually aligns correctly. Unsupported boss-clearance overhang defects recurred, but did not prevent the observed carriage fit. No physical stock TradRack selector exists yet.

| Physical item | Result / scope |
|---|---|
| Correct Ender carriage face | PASS, owner-observed |
| R7 seats on real carriage | PASS, owner-observed |
| Exercised carriage hole relationship | PASS, observed scope only |
| Visible wheel-fastener relationship | PASS, observed scope only |
| Boss clearance sufficient for seating | PASS, observed scope only |
| Boss-clearance unsupported-overhang print quality | DEFECT NOTED; not a seating failure |
| Selector-side fit | NOT TESTED |
| Belt/clamp dynamic clearance | NOT TESTED |
| Selector rocking/translation/rotation | NOT TESTED |
| Physical stand-off / tool access / loaded stiffness | NOT ESTABLISHED by this report |
| Full R7 physical PASS | NOT YET |

## Digital record before printing — not a new certification

- v0.2: 19/19 checks PASS.
- Candidate installed-selector check: no positive-volume interference reported for evaluated valid geometry; invalid source gear remained UNVERIFIED.
- Cable-cover nominal CAD clearance: 2.950 mm.
- Left selector-body nominal CAD clearance: 2.211 mm.
- Minimum window-to-pilot material: 0.975 mm, not certified strength.
- Candidate signed stand-off: +15.0 mm; NOT physically validated.

Evidence: local `outputs/ender-rack-r7-architecture-v2-20260904/manifest.json`. Hashes below identify the staged article files at documentation time. The owner's identification of the exact printed candidate is accepted; this is not independent proof that a particular G-code file was executed.

| Staged artifact | SHA-256 |
|---|---|
| `EnderRack_R7_ARCHITECTURE_V2_Candidate_001.step` | `211dd737f815708c13a3b893db18f45a31397b28b6dba2ba8a8c46da538f51cc` |
| `EnderRack_R7_ARCHITECTURE_V2_Candidate_001.stl` | `3f976add9b47ac424422b241242a32665b2b3c038427b2abf115d3fc5488bbd3` |
| `EnderRack_R7_ARCHITECTURE_V2_Candidate_001_E_PLATE_FACE_DOWN.step` | `a7f6751d69ed0f7f1a405b19c930a977331c63427a5b542f0489232f2b75046b` |
| `EnderRack_R7_ARCHITECTURE_V2_Candidate_001_E_PLATE_FACE_DOWN.stl` | `ed7fb8c7fa278a73bb028d01aa4eb59f7af653fbbaf37fdf5f1b80f93a545afd` |
| `EnderRack_R7_ARCHITECTURE_V2_Candidate_001_Voxelab_Aquila_0p4_PLA_220C_55C.gcode` | `ef1b904e6d0c422540dd8a2c84c911b99e0e558ad9afdffdc095a9fb02fee2b1` |


## Upgraded-skill audit caveat

FreeCAD skill commit `7c26a143d2a6e4318724b96cc71c297f7424efa0` found stale embedded context metadata, 48 unreconciled shape occurrences, hidden live-session generator dependencies and ineffective declared parameters. Earlier broad reproducibility/whole-assembly claims require re-audit before production. This task did not redo that audit. These findings neither erase the owner's physical fit observations nor make untested selector behavior PASS.

## Repository baseline and scope

At task start the original checkout and current remote main were both `3e33980e440dbcbaa9c4284f37c8e8d96db4fa81` (observed, not imposed). Original checkout had unstaged `.gitignore`, `README.md`, `docs/CURRENT_STATE.md`, `docs/DECISIONS.md`, `docs/ENDER_RACK_FRESH_THREAD_PROMPT.md`, `docs/ENDER_RACK_HANDOFF.md`, and untracked `tools/`, `verification/`. No staged edits were observed.

A fresh clone of actual current remote main was used for this documentation update, preserving that original checkout and all its unfinished verifier/tool work. No reset, history rewrite, old-baseline checkout or CAD modification. This commit documents the true state; it does not represent unreviewed local tool changes as released software. R7 design files remain staged externally, identified by hashes rather than silently regenerated.
