# EnderRack Source Correction

## Superseding milestone — 2026-09-01

**OFFICIAL ENDER-3 CARRIAGE INTERFACE — PHYSICAL R2 FIT-CHECK PASS**  
**15-LANE ENDER RACK — STATIC SELECTOR INTERFACE DESIGN RESUMED**

The exact successful R2 FCStd/STEP/STL and physical PASS photograph are preserved under `validated/ender3-carriage-interface-r2-pass/`. The official E plate now controls fabricated fit only for the physically validated hole pattern, seating face, orientation, and boss-clearance relationship. Bosses remain clearance features rather than locating datums.

`EnderRack_Selector_Interface_Coupon.FCStd` is the new static secondary coupon. It digitally passes reopen/export and local selector/wheel/conservative-belt checks. Physical real-selector testing is now the release gate. See `ENDER_RACK_SELECTOR_INTERFACE_COUPON.md`. No 238 mm sweep, lane structure, tensioner redesign, or production adapter was generated.

## Current project state

Historical state below is retained for traceability; it is superseded by the milestone above.

The Ender-3 V2 carriage reference remains rejected. The real plate corresponds closely to the official `E plate` when the correct rear face and in-plane orientation are used. Physical R1 testing confirmed the official hole pattern but found that the coupon could not seat over the two retained raised hotend bosses. R2 preserves the pattern and adds pockets from user-measured Ø5 × 5 mm boss geometry. See `ENDER3_OFFICIAL_CARRIAGE_REAUDIT.md` and `ENDER3_OFFICIAL_CARRIAGE_COUPON_R2.md`. No adapter, selector transform, production EnderRack derivative, or tensioner redesign was generated.

## Decision summary

| Question | Result | Evidence / effect |
|---|---|---|
| Was the prior V2 work preserved? | PASS | 30 immutable copies are recorded in `archive/rejected-ender3v2-reference/archive_manifest.json`; originals remain in place. |
| Was official Ender-3 CAD used? | PASS | Exact repository commit and Git blob identities are recorded below. |
| Did the complete STEP import through FreeCAD MCP? | PASS | 1,243 objects; 1,178 shape-bearing objects; no null shapes, invalid topology, or invalid placements. |
| Did the FCStd survive save/close/reopen/recompute? | PASS | 1,243 objects and the embedded provenance record persisted. |
| Was the official X gantry isolated? | PASS | `EnderRack_Ender3_Official_Concept.FCStd` contains the `Ender3_X_Gantry_Official` group and 33 self-contained, valid shape copies. |
| Does the official plate match the real plate? | **PASS — visually provisional** | New photo evidence matches the rear/photo-oriented official `E plate` outline, three-wheel pattern, auxiliary holes, integral hotend bosses, and separate belt hardware. Physical dimensions are still gated by the coupon. |
| Did R1 correlate physically? | **CONDITIONAL PASS** | Hole pattern aligns; flat seating failed solely because the retained raised bosses lacked relief pockets. |
| Was an R2 printable coupon exported? | **PASS — digital** | Versioned FCStd, STEP, and STL retain R1 coordinates and add two physically dimensioned boss pockets. Physical R2 seating remains pending. |

## Rejected Ender-3 V2 work

Archive: `archive/rejected-ender3v2-reference/`

Status label: **REJECTED — WRONG MACHINE REFERENCE — ENDER-3 V2**

The archive contains 30 files, including the original community V2 STEP, V2 reference FCStd, V2-based concepts/designs, failed coupon FCStd/STEP/STL, screenshots, audits, and recovery records. `archive_manifest.json` records each source path, archived path, byte size, source timestamp, and SHA-256. The archived files are read-only copies; the originals were not deleted or modified.

New physical evidence is preserved as `interface-recovery/evidence/physical_plate_rear_2026-08-31.jpg`, SHA-256 `AA6078E69A8E5B0F2A0D393312A3B4198EC32DB7804CC294B9D424CF7C9D427F`.

## Official source provenance

Repository: [Creality3DPrinting/Ender-3](https://github.com/Creality3DPrinting/Ender-3)

Repository commit: `88c7758cea9d0d00a54fdb238bedb3b33425f409`

| Source | Repository path / identity | Bytes | SHA-256 | Local status |
|---|---|---:|---|---|
| `Ender3.STEP` | [`Ender-3 Mechanical/STP/Ender3.STEP`](https://github.com/Creality3DPrinting/Ender-3/blob/88c7758cea9d0d00a54fdb238bedb3b33425f409/Ender-3%20Mechanical/STP/Ender3.STEP); Git blob `30c9b930c0cc094b4d02acd72d71d835d7225c72` | 29,867,304 | `7E868F30A44F0E6B1DD0DAF8AF1D7810AD9A754CC6FA066F6EF4D2B81E3297AF` | Immutable/read-only |
| `Ender 3.f3d` | [`Ender-3 Mechanical/F360/Ender 3.f3d`](https://github.com/Creality3DPrinting/Ender-3/blob/88c7758cea9d0d00a54fdb238bedb3b33425f409/Ender-3%20Mechanical/F360/Ender%203.f3d); Git blob `998bd68bf940c3bd691fa9d7ead705bfa401e323` | 6,344,736 | `95909A53CCFAC0E4F3EFEC9B964780D5602B453F441274DFEBB4B5D18C2BC726` | Recorded and immutable/read-only; not imported |

Retrieved: `2026-08-31T18:06:44-06:00` (America/Denver).

Local source directory: `work/sources/ender-rack/official-ender3/`

The prior community Ender-3 V2 model was not used as a fallback.

## FreeCAD MCP import and digital validation

Deliverable: `Ender3_Official_reference.FCStd`

| Check | Result |
|---|---|
| MCP/RPC transport | PASS — listener verified at `127.0.0.1:9875`; no remote/wildcard binding |
| Imported document objects | 1,243 |
| Shape-bearing objects | 1,178 |
| Null geometry | 0 |
| Invalid topology | 0 |
| Invalid placements | 0 |
| Save/close/reopen/recompute | PASS |
| Reopened object count | 1,243 |
| Embedded source provenance | PASS |
| Obvious incomplete assembly | Not observed; frame, axes, belts, motors, endstops, bed, electronics, and hotend/fan assembly are present |

Intentional construction axes and origins were accepted. Their mathematically infinite bounding boxes were excluded from physical size calculations; they are not geometry failures.

Inventory: `../../work/ender-rack-inventory/ender3_official_import.json`

FCStd SHA-256: `56668B32302299CBFA9208167C4F50BA45C22BB1780F3A8E5E185FEA3840C75B`

## Official X carriage audit

The official assembly labels the sole carriage-plate candidate `E plate` (`Part__Feature286`). It is adjacent to the three X-stage V-wheels, X extrusion, X belt, hotend/fan assembly, belt clamps, motor, and endstop.

Measured directly from the imported BRep:

| Feature | Official CAD value |
|---|---:|
| Overall `E plate` bounding box | 64.000 × 63.949 × 27.400 mm |
| Plate base thickness between principal parallel faces | 2.500 mm |
| Upper wheel-axis center distance | 40.000 mm |
| Upper wheel line to lower/eccentric axis | 40.200 mm |
| Upper wheel through-hole diameter | 5.000 mm |
| Lower/eccentric through-hole diameter | 7.200 mm |
| Shape validity | PASS |

The official front view is [Ender3_Official_E_Plate_Face.png](screenshots/Ender3_Official_E_Plate_Face.png). The isolated stage is [Ender3_X_Gantry_Official.png](screenshots/Ender3_X_Gantry_Official.png).

### Physical correspondence gate — re-audited

New photographic evidence shows the physical carriage in the same orientation as the official rear view. The earlier rejection compared opposite faces and incorrectly required separate assembly hardware to be part of the bare plate solid.

- `Copper cover002/003` are separate gold belt-end/crimp objects visible above the rear plate face.
- The two 14 mm-spaced hotend bosses are integral counterbored/embossed topology in `E plate`.
- `M3X16 Pan Head Screw003/004` are separate hotend/radiator fasteners in `Sprinkler_assembly` and align with those bosses.
- Outline, three-wheel pattern, auxiliary holes, and hardware locations visually correspond.

The official plate therefore passes the visual gate and is promoted to **physical fit-check candidate**, not production reference. The photograph is perspective evidence; the printed coupon remains the dimensional gate. See [the front/rear comparison](screenshots/Ender3_Official_Carriage_FRONT-left_REAR-right.png) and `ENDER3_OFFICIAL_CARRIAGE_REAUDIT.md`.

## Official X-gantry working concept

Deliverable: `EnderRack_Ender3_Official_Concept.FCStd`

The `Ender3_X_Gantry_Official` group contains self-contained copies divided into:

- `Carriage_Plate_and_Wheels`
- `X_Extrusion_and_Belt`
- `X_Motor_and_Endstop`
- `X_Idler_and_Adjuster`

All 33 copied shape objects reopened validly and contain source-object metadata. The concept is labeled as official-reference geometry requiring physical verification; it is not a production EnderRack design.

Concept FCStd SHA-256: `55AEBD08090A8AA736FAB293295D40DA848D3648BA6094E3BDDE4B71E6C3302A`

## Coupon and production release status

R1 (`Ender3_Official_Carriage_FitCheck.FCStd`, STEP, and STL) remains preserved as the physical hole-correlation/boss-interference artifact. Its hole pattern passed, but the 2.0 mm plate could not seat over the retained bosses.

R2 (`Ender3_Official_Carriage_FitCheck_R2.FCStd`, STEP, and STL) keeps the 56.5 × 32.9 mm outline, four source-derived holes, wheel reliefs, V-notch, and cross. It adds two Ø5.5 × 5.2 mm-deep pockets based on the user's Ø5 × 5 mm physical boss measurements, leaves a 1.2 mm floor, and increases total thickness to 6.4 mm. It reopened as one valid solid; STEP and STL fidelity checks passed. Physical R2 seating remains the release gate.

No `EnderRack_15Lane_Ender3.FCStd` was created. No production adapter or production tensioner fabrication is authorized.

Print only R2 in PLA for fit-check use. PASS promotes the official plate to the EnderRack carriage reference. If it fails, document the exact interference and remeasure the controlling feature before changing geometry. A measured replacement carriage reference is not justified unless the corrected official interface still fails:

- `Y=0`: real outward steel mounting face;
- `X`: line through the two upper wheel axes;
- origin: motor-side upper wheel axis;
- `+X`: toward the tensioner;
- in-plane scan calibration: independent X and Z bars/cross;
- hole spacing: pin/bolt/drill-shank center-distance measurements where possible;
- depth and raised features: calipers/depth measurements, never inferred from the scan.

## Preserved conclusions and measurements

These remain valid or provisional independently of the rejected V2 carriage interface:

| Item | Status |
|---|---|
| Official TradRack R1 reference and selector geometry | Preserved |
| 17 mm lane pitch | Preserved; high confidence |
| 15-lane target / 238 mm first-to-last span | Preserved |
| 12-lane fallback / 187 mm first-to-last span | Preserved |
| Approx. 270 mm physical X-carriage travel / 135 mm midpoint | Preserved, provisional, medium-high confidence |
| Approx. 45 mm tensioner length | Preserved, provisional, low confidence |
| Approx. 7 mm tensioner protrusion | Preserved, provisional, low confidence; datum must be restated |
| Approx. 10 mm belt center on 20 mm extrusion | Preserved, provisional, low confidence; datum must be restated |
| Approx. 10 mm pulley center from extrusion end | Preserved, provisional, low-medium confidence |
| 15/12-lane parametric architecture | Preserved |
| Happy Hare/Klipper and electronics concept | Preserved; controller identity still unknown |

The detailed per-value provenance and datum notes remain in `interface-recovery/retained_physical_evidence.csv` and `interface-recovery/Physical_Interface_Parameters.csv`.

## Conclusions that must be recomputed

After the official-CAD coupon passes physical validation, recompute:

- carriage-to-selector rigid transform;
- adapter geometry and stand-off;
- mounting-hole use and fastener access;
- belt and belt-clamp clearance;
- cable routing;
- stock tensioner collision;
- endstop interaction;
- first/middle/last lane collision envelope;
- selector-position repeatability on the V-wheel stage.

All V2-derived selector offsets, hole coordinates, interface clearances, and tensioner collision conclusions remain rejected.

## Machine identity / upgrade audit

- **Mechanical identity:** Ender-3-family donor; official `E plate` visually correlated, physical coupon confirmation pending.
- **Display:** apparently non-original or later-style; not used for mechanical identification.
- **Controller board:** unknown until physically inspected.
- **Other upgrades:** unknown unless physically observed.

Electronics appearance did not affect the mechanical-source selection.
