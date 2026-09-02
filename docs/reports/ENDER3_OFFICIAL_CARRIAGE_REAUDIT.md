# Ender-3 Official Carriage Re-audit

## Superseding physical result — 2026-09-01

**R2 PHYSICAL FIT-CHECK PASS.** The official E plate is promoted as the controlling fabricated-fit reference only for the hole pattern, seating face, orientation, and boss-clearance relationship exercised by R2. The exact successful artifacts and PASS photograph are preserved under `validated/ender3-carriage-interface-r2-pass/`.

The R2 pockets are Ø5.5 × 5.2 mm deep. The 5 × 5 mm derivation values are successful nominal coupon inputs, not independently measured boss dimensions. The bosses are clearance features, not precision locators.

Static selector-interface work has resumed in `EnderRack_Selector_Interface_Coupon.FCStd`; physical real-selector testing is the current release gate. The historical re-audit narrative below is retained for traceability.

## Outcome

**PASS — the new physical photograph visually correlates with the official Creality Ender-3 `E plate` and complete carriage assembly when the correct plate face and orientation are used.**

This supersedes the earlier visual rejection. That rejection compared the wrong/opposite face and treated separate assembly hardware as if it had to be topology of the bare plate.

The official carriage remains at **physical fit-check candidate** status. R1 confirmed the hole pattern but failed to seat because it omitted relief for the two retained hotend bosses. Production adapter work remains blocked until the R2 coupon passes on the real machine.

## R1 physical result and R2 recovery — 2026-09-01

New physical evidence establishes a narrower result than either the original rejection or an unconditional pass:

- R1 official-CAD hole-pattern correlation: **PASS**;
- R1 flat seating: **FAIL — two retained raised hotend bosses obstruct the coupon**;
- boss removal: **not authorized**; they are treated as integral/retained carriage features;
- user-measured boss size: **Ø5.0 × 5.0 mm high**;
- gold belt hardware: separate assembly components, unchanged;
- R2 digital model/export validation: **PASS**;
- R2 physical seating: **PENDING**.

R2 adds two Ø5.5 × 5.2 mm-deep pockets on the same 14.0 mm source-derived centers. A 1.2 mm floor produces a 6.4 mm coupon thickness. Hole centers, Ø3.4 mm bores, wheel reliefs, outline, and datum marks are unchanged. See `ENDER3_OFFICIAL_CARRIAGE_COUPON_R2.md`.

## Physical evidence

Evidence file: `interface-recovery/evidence/physical_plate_rear_2026-08-31.jpg`

SHA-256: `AA6078E69A8E5B0F2A0D393312A3B4198EC32DB7804CC294B9D424CF7C9D427F`

The photograph is perspective evidence rather than a calibrated dimensional image. It supports correspondence of:

- overall rounded rectangular outline and central wheel tab;
- three-wheel triangular pattern;
- two 14 mm-spaced hotend-mount features;
- asymmetric auxiliary holes;
- wheel fasteners;
- two gold rear raised components associated with the belt.

## Face and orientation correspondence

| Physical/CAD view | Correspondence |
|---|---|
| Photograph | Rear / wheel-and-belt face of the physical carriage, with the central wheel tab upward |
| Imported model | `Part__Feature286`, label `E plate` |
| Matching CAD camera | Top view of the imported assembly with a 180° in-plane roll |
| Opposite face | Bottom view; hotend/radiator attachment face |

The combined render is [Ender3_Official_Carriage_FRONT-left_REAR-right.png](screenshots/Ender3_Official_Carriage_FRONT-left_REAR-right.png): **front is left; rear/photo-corresponding face is right**.

Individual renders:

- [Front / hotend face](screenshots/Ender3_Official_Carriage_FRONT_PhotoOrientation.png)
- [Rear / photo-corresponding face](screenshots/Ender3_Official_Carriage_REAR_PhotoOrientation.png)

## Complete-assembly feature audit

The apparent raised features are split between integral plate topology and separate assembly components:

| Feature | Official object(s) | Finding |
|---|---|---|
| Bare steel plate | `Part__Feature286` / `E plate` | One valid solid; controls fabricated-fit hole positions and plate outline |
| Two 14 mm-spaced hotend mounting bosses | Integral faces of `E plate` | Embossed/counterbored plate topology, not separate standoff objects |
| Hotend/radiator attachment screws | `Part__Feature663`, `Part__Feature664` | Separate `M3X16 Pan Head Screw003/004` objects inside `Sprinkler_assembly`; aligned to the integral boss centers |
| Gold raised rear pieces | `Part__Feature631`, `Part__Feature632` | Separate `Copper cover002/003` belt-end/crimp hardware; not hotend standoffs |
| Wheel hardware | `Part__Feature287–293`, `384–386` | Separate screws, washer, eccentric column, spacers, and nuts |

The official hotend-mount center spacing is exactly `14.000 mm`. The upper wheel-axis spacing is `40.000 mm`, and the eccentric axis is `40.200 mm` from the upper-wheel line.

Detailed machine-readable results: `../../work/ender-rack-inventory/ender3_official_carriage_reaudit.json`.

## Official-CAD fit-check coupon

Generated through FreeCAD MCP directly from cylindrical faces of the imported `E plate` BRep:

- `Ender3_Official_Carriage_FitCheck.FCStd`
- `exports/Ender3_Official_Carriage_FitCheck.step`
- `exports/Ender3_Official_Carriage_FitCheck.stl`
- [Coupon render](screenshots/Ender3_Official_Carriage_FitCheck.png)

The coupon is a rear-face pattern overlay, not an adapter. It contains:

- both 14 mm-spaced hotend-mount holes;
- both asymmetric auxiliary holes visible in the official plate pattern;
- reliefs derived from the installed upper-wheel fastener envelopes;
- a V-notch marking the official idler/tensioner side;
- an engraved cross marking the official motor side;
- no TradRack, selector, tensioner, or production structure.

Dimensions and digital verification:

| Check | Result |
|---|---:|
| Coupon bounding box | 56.500 × 32.900 × 2.000 mm |
| Selected source-derived holes | 4 |
| Nominal source bores | Ø3.000 mm |
| Printed clearance bores | Ø3.400 mm |
| Upper-wheel hardware relief radius | 5.750 mm |
| Coupon topology | PASS — one valid solid |
| Save/close/reopen/recompute | PASS |
| STEP BRep distance from FCStd | `7.42e-14 mm` |
| STEP maximum bounding-box delta | `2.84e-14 mm` |
| STL maximum bounding-box delta | `5.72e-7 mm` |
| STL facets | 716 |

Hashes:

| File | Bytes | SHA-256 |
|---|---:|---|
| `Ender3_Official_Carriage_FitCheck.FCStd` | 24,627 | `C4175A7755547D9A2DB97604E42E94CEBF9F6A8A2A187A6B5E917BBEA12FC36B` |
| `Ender3_Official_Carriage_FitCheck.step` | 40,021 | `900BCF148CB706E4676D125A6EC9DDD5D4752B4ED1A51B1910FBE4BFE2A1C3CD` |
| `Ender3_Official_Carriage_FitCheck.stl` | 35,884 | `946469AD81B78B434278A1850FFD6336486A68D2CAEA35CC339B86701350E609` |

Machine-readable verification: `../../work/ender-rack-inventory/ender3_official_fitcheck_verification.json`.

## R2 physical fit-check instructions

Fabrication status: **PROVISIONAL — FIT-CHECK FABRICATION ONLY. DO NOT FABRICATE PRODUCTION PARTS.**

Do not reprint R1. Print `exports/Ender3_Official_Carriage_FitCheck_R2.stl` cheaply in PLA with a 0.4 mm nozzle and 0.2 mm layers. Do not apply slicer XY/hole compensation on the first test. Import at 100% scale and flip the part so the two boss pockets face upward.

Test against the same rear/photo-corresponding face used for the re-audit:

1. Orient the V-notch toward the official idler/tensioner side and the engraved cross toward the motor side.
2. Confirm both retained bosses enter the new pockets without force.
3. Confirm the two large open reliefs clear the installed upper-wheel fastener hardware.
4. Confirm both hotend-mount holes align and accept pins/fasteners finger-snug without forcing.
5. Use the two auxiliary holes as positional pattern checks; do not assume they are threaded or force fasteners into them.
6. Confirm the coupon seats flat without rocking.
7. With the coupon held finger-snug, confirm the V-notch/cross cannot translate or rotate appreciably relative to the wheel-axis pattern.

PASS promotes the official `E plate` to the EnderRack carriage reference. FAIL stops adapter work and requires recording the exact R2 interference and remeasuring the controlling feature before any geometry is changed.

No `EnderRack_15Lane_Ender3.FCStd`, production adapter, or tensioner redesign was created during this re-audit.

## Project state

**ENDER RACK ARCHITECTURE PRESERVED — R1 HOLE PATTERN PASS / BOSS SEATING FAIL — R2 DIGITAL PASS — R2 PHYSICAL FIT-CHECK PENDING**
