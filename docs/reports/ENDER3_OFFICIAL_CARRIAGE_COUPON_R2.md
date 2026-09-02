# Ender-3 Official Carriage Coupon R2

## Status

**PHYSICAL FIT-CHECK PASS — 2026-09-01**

Fabrication status: **PROVISIONAL — FIT-CHECK FABRICATION ONLY. DO NOT FABRICATE PRODUCTION PARTS.**

The R1 coupon established good physical hole-pattern correlation but could not seat flat because it omitted relief for the two retained, raised hotend bosses. R2 changes only the coupon thickness and adds two coaxial boss pockets. The official plate reference, hole centers, wheel reliefs, V-notch, and motor-side cross are unchanged.

## Controlling dimensions

| Parameter | Value | Source |
|---|---:|---|
| Boss count | 2 | Physical observation / official assembly correlation |
| Boss center spacing | 14.000 mm | Official `E plate` BRep |
| Nominal boss-envelope input | 5.000 × 5.000 mm | Successful R2 design input; not an independent boss measurement |
| Pocket diameter | 5.500 mm | R2 geometry physically passed |
| Pocket depth | 5.200 mm | R2 geometry physically passed |
| Remaining floor | 1.200 mm | Fit-check design parameter |
| Coupon thickness | 6.400 mm | Pocket depth + floor |
| Through holes | Ø3.400 mm | Unchanged from R1 |

The physical seating result controls R2. The actual boss diameter and height were not independently measured, so the bosses remain clearance features rather than precision locators.

## Deliverables and verification

| Artifact | Bytes | SHA-256 |
|---|---:|---|
| `Ender3_Official_Carriage_FitCheck_R2.FCStd` | 27,839 | `5BFCCEA429CA99938D7D4C6E331EAB8527BCAC78F001BD873B6BBEB9D56F6B39` |
| `exports/Ender3_Official_Carriage_FitCheck_R2.step` | 43,823 | `CEB0FF7112BBFD7E4EDBA46C828C431A68E6472DCBF275925C5A48B8941B4AFC` |
| `exports/Ender3_Official_Carriage_FitCheck_R2.stl` | 46,284 | `E57E049BD18FC0F773B481B130ADC6976BBFF6C08E0909EE653916B485F3D88B` |
| `screenshots/Ender3_Official_Carriage_FitCheck_R2.png` | 21,190 | `52B99C8099405AFC99566D720B2FF6B1E23C5563844029B8EB56C96636DDB788` |

| Check | Result |
|---|---:|
| Bounding box | 56.500 × 32.900 × 6.400 mm |
| Topology | PASS — one valid solid |
| Save/close/reopen/recompute | PASS |
| Parameter object persisted | PASS |
| Reopened BRep pocket cylinders | PASS — 2 × R2.750, Z=0.000–5.200 mm |
| STEP BRep distance | `9.53e-17 mm` |
| STEP maximum bounding-box delta | `2.84e-14 mm` |
| STL maximum bounding-box delta | `5.72e-7 mm` |
| STL facets | 924 |
| RPC binding during generation | PASS — `127.0.0.1:9875` only |

Machine-readable verification: `../../work/ender-rack-inventory/ender3_official_fitcheck_r2_verification.json`.

## Print and physical test

Print the STL in PLA with a 0.4 mm nozzle and 0.2 mm layers. Import at 100% scale with no initial XY or hole compensation. Flip the part in the slicer so the two boss pockets face upward.

1. Put the V-notch toward the idler/tensioner side and the engraved cross toward the motor side.
2. Confirm both retained bosses enter the pockets without force.
3. Confirm all four pattern holes remain aligned.
4. Confirm the coupon seats flat against the steel face without rocking.
5. Hold or tighten it finger-snug and verify the datum marks cannot translate or rotate appreciably.
6. Confirm the wheel and separate gold belt hardware remain clear.

All six checks were reported as passing. The exact FCStd/STEP/STL and the received PASS photograph are preserved under `validated/ender3-carriage-interface-r2-pass/` with SHA-256 hashes.

No adapter, tensioner, selector transform, lane model, or production component was changed.
