> Historical evidence only. Not the current design or print instruction. R5 relationships and 22.25 mm stand-off are retired; see docs/CURRENT_STATE.md.

# EnderRack Mechanical Feasibility Audit

> **LEGACY / SUPERSEDED:** This report uses the rejected Ender-3 V2 carriage reference. Preserve its TradRack and lane-analysis evidence only. Do not use its carriage coordinates, transforms, adapter geometry, or collision conclusions for fabrication.

> **2026-08-31 PHYSICAL INTERFACE CORRECTION:** The printed carriage coupon did not match the plate on this machine. The subsequent forensic audit proved that the digital E1–E5 center pipeline was faithful but that the community carriage interface is incompatible with the physical specimen and its source features were oversimplified. All carriage-interface-dependent transforms and collisions are superseded. Independent physical travel/tensioner evidence and official TradRack geometry remain valid at their recorded confidence. See [`interface-recovery/ENDER_CARRIAGE_INTERFACE_AUDIT.md`](interface-recovery/ENDER_CARRIAGE_INTERFACE_AUDIT.md).

## 2026-08-31 design-phase rebaseline

This section supersedes the earlier lane recommendation and interface-overlap conclusions below. The original feasibility record remains intact for traceability. Detailed implementation and verification results are in `ENDER_RACK_DESIGN_REPORT.md`.

**Release state: PROVISIONAL — FIT-CHECK FABRICATION ONLY. DO NOT FABRICATE PRODUCTION PARTS.**

| Question | Updated result | Design-phase conclusion |
|---|---|---|
| Can the Ender X stage replace MGN9? | **CONDITIONAL YES** | The parametric conversion is viable at center and the interface adapter is a valid single solid. Production use is gated by a left-end selector/tensioner interference, physical travel/endstop measurements, and repeatability testing. |
| Can the stock selector remain essentially unchanged? | **CONDITIONAL** | The drive, servo, filament path, lane modules, and main selector structure remain stock. Two interface fasteners and the stock cable-chain anchor require replacement. The lower selector motor mount conflicts with the stock Ender tensioner at left-side lane positions; resolve with a measured low-profile tensioner or a separately approved larger stand-off. |
| What transform is implemented? | **PROVISIONAL** | `T_EnderCarriage_From_TradRackSelector = [X 0.000, Y +13.5529, Z -9.3850 mm; roll/pitch/yaw 0°]`. This is the reference alignment plus a controlled +8.250 mm outward adjustment. |
| How many lanes are targeted? | **15 TARGET / 12 FALLBACK / 16 NOT RELEASED** | At 17 mm pitch: 15 requires 238 mm and leaves 32 mm gross within the rough 270 mm observation; 12 requires 187 mm; 16 requires 255 mm and leaves only 15 mm gross. The exact left-end packaging conflict affects both the centered 15- and 12-lane visualizations, so neither is production-cleared yet. |
| What must be verified next? | **PHYSICAL GATES REMAIN** | Accurate switch-click-to-safe-opposite travel, asymmetric end reserves, carriage holes/face, belt and tensioner geometry, selector mass, harness routing, and first/middle/last-lane repeatability. |

The 270 mm center-hole observation is useful but remains a rough physical measurement. `ArrayOffset` therefore remains editable and centered only for visualization; it must eventually maximize the smaller verified end clearance rather than enforce symmetry.

The design document adds a parametric 15/12/16 lane array, a relieved carriage adapter, removable trigger concept, service-clearance volumes, and a fit-check-only derivative. Exact BRep checks found zero center-position collision after excluding components explicitly classified for replacement. At the centered 15-lane first extreme, the stock lower selector motor mount intersects the stock Ender tensioner housing, and moving the selector farther outward by approximately 15 mm beyond the implemented offset was required to clear it in a probe. That larger change was not adopted because it exceeds the approved small controlled optimization and would require new module-mounting provisions.

![15-lane design](screenshots/07-ender-rack-15-lane-design.png)

![Parametric adapter interface](screenshots/08-adapter-interface-closeup.png)

![Fit-check derivative](screenshots/11-interface-fitcheck-part.png)

Generated 2026-08-30 with FreeCAD 1.1.3 and FreeCAD MCP 0.1.22. All CAD imports, isolation, measurements, collision checks, document saves, reopening, and screenshots were performed through the local FreeCAD MCP connection on `127.0.0.1:9875`.

## Executive conclusion

| Question | Result | Mechanical conclusion |
|---|---|---|
| Can the complete Ender X linear stage replace the MGN9 stage? | **CONDITIONAL YES** | The modeled Ender stage provides 251.742 mm of collision-limited CAD travel and carries the selector through the tested lane positions. The community Ender model does not provide a trustworthy belt strand, wiring envelope, or usable endstop/homing range, so real-machine validation is mandatory. |
| Can the stock TradRack selector remain essentially unchanged? | **CONDITIONAL** | The drive core, motor, servo, filament path, sensor, and lane modules can remain stock. The MGN9 rail/carriage are removed. At the extrusion-aligned interface, two printed carriage pieces and two fasteners intersect the Ender plate; local relief/stand-off and fastener substitution are required. |
| What interface transformation is required? | **PROVISIONAL REFERENCE** | In the normalized Ender carriage frame: **X 0.000 mm, Y +5.303 mm, Z −9.385 mm; roll/pitch/yaw 0°**. This aligns the two 20×20 extrusion centerlines and parallel travel axes. It preserves stock lane geometry but leaves 64.723 mm³ of localized interface overlap to resolve during adapter design. |
| How many lanes fit? | **8 PASS / 12 PASS / 15 CAD-MAX** | Module mounting length supports 19 positions; modeled selector travel is the first constraint at 15. Twelve lanes is the provisional physical-verification-gated recommendation. |
| What must be measured physically? | **SEE PRIORITY LIST** | Carriage holes/face, wheel geometry, extrusion, belt, endstop/homing range, and plate-to-V-slot datums are the gating measurements. |

This phase does **not** establish production readiness or dynamic load capacity. It establishes that the geometry is promising and identifies the exact uncertainties the next phase must close.

## Source provenance and import status

### TradRack

- Source repository: <https://github.com/Annex-Engineering/TradRack>
- Repository `main` commit at download: `f89dc0b115adfc49195d782c5d7ecd348a574891`
- Git blob: `c1dbef9f292f7f7a3bec446b092be2f23ef4702f`
- Archive: `Trad_Rack_R1_2024-03-04_STEP.7z`
- Archive size: 91,473,657 bytes
- Archive SHA-256: `BE7646216D6483DA49B548B7225BF3A64F07A12960D89EE659F0D2CCB5F271E8`
- Imported baseline: `trad_rack_(default).STEP`
- STEP size: 116,600,287 bytes
- STEP SHA-256: `19459C5098A6C084D50F77AB4FBDBFABAB48D6845C84B3E9159F50776083BDB3`
- Import: **PASS**, 1,812 FreeCAD objects. No null imported shapes and no invalid topology found in the full validation pass.

The archive also contains official 6 mm belt, 9 g servo, NEMA 14, and breakout-board variants. They were recorded but not mixed into the default baseline.

### Ender-3 V2

- Preferred Printables page: <https://www.printables.com/model/255019-ender-3-v2-step-file-for-easy-modification-and-design>
- Preferred-page automation result: HTTP 403, so the supplied mirror was used.
- Mirror: <https://www.dropbox.com/s/cl4yxvw00t8knvq/Creality-Ender3-V2-rev4.STEP?dl=1>
- File: `Creality-Ender3-V2-rev4.STEP`
- Size: 36,580,869 bytes
- SHA-256 provenance record: `D81BDE4587B3237FDA23515AD524482A8F0D153226B952A3B3734CBC29D3B5D0`
- Import: **PASS**, 537 FreeCAD objects. No null Part features; targeted X-gantry, plate, and wheel topology checks passed.

The Ender file is community CAD, not authoritative Creality mechanical CAD. Its hash records what was analyzed; it does not certify dimensional accuracy.

## Coordinate systems and interface

The concept uses a right-handed Ender carriage frame:

- **+X:** carriage travel along the X extrusion
- **+Y:** outward from the Ender carriage mounting face toward the TradRack selector
- **+Z:** physical up
- **Origin:** centroid of the selected carriage-interface cylindrical features, projected onto the outward plate face

The TradRack selector frame is centered on the outward face of the MGN9 carriage with +X along the stock rail. The reference transform was obtained by aligning the stock TradRack and Ender 20×20 extrusion centerlines while keeping their travel axes parallel.

| Component | X | Y | Z / other |
|---|---:|---:|---:|
| Provisional TradRack-frame translation | 0.000 mm | +5.303 mm | −9.385 mm |
| Rotation | 0° roll | 0° pitch | 0° yaw |
| MGN9 carriage mounting pattern | 10.000 mm | 15.000 mm | Four nominal Ø3 mm axes |
| Ender plate thickness | — | 2.500 mm | Parallel major-face separation |
| Inferred Ender belt centerline | — | −15.256 mm | Z −9.397 mm |

The continuous Ender belt strand is absent from the community STEP. Its centerline is inferred from the motor pulley and two idler-bearing centers and must be checked physically.

### Interface interference

The extrusion-aligned transform has 64.723 mm³ of exact BRep intersection:

| Ender component | TradRack component | Intersection |
|---|---|---:|
| Metal hotend carriage plate | Carriage Middle, 9 mm belt C-cart | 5.321 mm³ |
| Metal hotend carriage plate | Carriage Left | 1.536 mm³ |
| Metal hotend carriage plate / one V-wheel | M5×10 socket-head fastener | 43.259 mm³ total |
| Metal hotend carriage plate | M3×8 socket-head fastener | 14.607 mm³ |

Moving the complete TradRack reference outward by up to 10 mm did not produce a clean no-intersection state, because stock carriage geometry extends behind its MGN interface plane. A simple rigid stand-off therefore does not make the assembly drop-in while preserving the stock lane/extrusion relationship. The adapter phase must provide local relief and replace/reorient the two interfering fasteners; the two printed carriage parts may need local revision if relief cannot be contained in the adapter.

![Interface close-up](screenshots/04-interface-closeup.png)

## Ender carriage measurements

### Wheel and plate geometry

Wheel centers in the Ender carriage frame:

| Wheel | X | Z |
|---|---:|---:|
| Upper/first wheel (`Part__Feature192`) | +33.300 mm | +11.878 mm |
| Eccentric/lower wheel (`Part__Feature193`) | +13.300 mm | −28.122 mm |
| Upper/third wheel (`Part__Feature194`) | −6.700 mm | +11.878 mm |

Center distances are 40.000 mm between the two aligned wheels and 44.721 mm from each aligned wheel to the eccentric wheel. The modeled eccentric spacer center is approximately X +13.946 mm, Z −27.453 mm. These are high-priority caliper checks.

The plate contains several cylindrical holes, counterbores, and bosses. Their complete measured coordinates and diameters are stored in `Dimensional_Audit`; they must not all be assumed to be available adapter fasteners until the physical plate is checked. The most relevant non-wheel candidate axes include nominal Ø3.00, Ø3.02, Ø4.00, and concentric Ø5.27 features.

### Donor-stage envelope

- Ender X extrusion: **345.000 × 20.000 × 20.000 mm**
- Donor carriage/plate/wheel envelope: approximately **37.740 × 64.080 × 64.080 mm** in imported world-envelope order
- Ender X belt strand: **not modeled**
- Wiring/harness flex envelope: **not modeled**

![Isolated Ender donor](screenshots/01-ender-x-gantry-donor.png)

## Travel and lane capacity

### Travel

| Quantity | Result | Meaning |
|---|---:|---|
| Wheel-on-extrusion geometric delta range | −169.150 to +111.773 mm | Wheel centers remain on modeled extrusion |
| Raw CAD travel | **252.242 mm** | Wheel-track limit plus exact fixed-end collision checks |
| Usable modeled selector travel | **251.742 mm** | Combined donor + selector, 0.25 mm inside each modeled limit |
| First-end clearance at usable limit | 0.023 mm | Essentially a CAD contact limit, not a production clearance |
| Other-end clearance at usable limit | 2.006 mm | Modeled BRep clearance |

The modeled plate did not positively actuate the endstop lever before the wheel-track limit. Therefore the 251.742 mm value is **not a verified homed operating range**. Real endstop trigger, switch overtravel, belt clamp, and homing overshoot will reduce it.

### Independent capacity constraints

- Measured TradRack lane pitch: **17.000 mm**
- Transformed lane-module X envelope: **19.007 mm**
- Collision-free module-center interval: **−161.385 to +146.615 mm**
- Module-mounting capacity: **19 lanes**
- Selector-travel capacity: **15 lanes**
- First limiting constraint: **selector travel**

| Lane count | First-to-last center travel | Extreme collision check | Result |
|---:|---:|---|---|
| 8 | 119.000 mm | Both extremes clear | **PASS** |
| 12 | 187.000 mm | Both extremes clear | **PASS** |
| 15 | 238.000 mm | Both extremes clear in community CAD | **CAD PASS / PHYSICALLY UNVERIFIED** |

Removing 5 mm from both modeled travel ends still produces a pitch calculation of 15 lanes, but only about 3.7 mm of total pitch headroom remains beyond the 238 mm requirement. Because the modeled endstop result is unusable and one extreme is nearly in contact, **12 lanes is the provisional recommendation** until real usable travel is measured. Fifteen is the geometric maximum, not a build recommendation.

![First modeled selector extreme](screenshots/05-selector-first-extreme.png)

![Last modeled selector extreme](screenshots/06-selector-last-extreme.png)

## TradRack change classification

### Unchanged

- Filament drive core and NEMA17 drive motor
- Servo and servo mechanism
- Filament sensor and ECAS/output path geometry
- Lane-module bodies, bearings, and 17 mm pitch
- Most selector printed structure and hardware
- End modules, subject to the Ender end-hardware collision check

### Repositioned only

- Lane-module bank onto the Ender 20×20 reference extrusion
- Selector belt system and end attachments
- Cable chain or replacement harness routing; the imported chain is not a valid rigid-motion collision envelope

### Replacement or local revision required

- New Ender-carriage-to-selector adapter
- M5×10 and M3×8 fasteners that intersect the Ender plate
- Local clearance for `Carriage Middle` and `Carriage Left`; revise those pieces only if the adapter cannot provide the relief

### Possibly unnecessary

- MGN9 rail and carriage
- Stock TradRack 280 mm extrusion, because its 20×20 centerline was mapped onto the Ender extrusion
- MGN9 rail stop
- Original K3 mounting brackets

![Isolated TradRack selector reference](screenshots/02-tradrack-selector-reference.png)

![Combined concept](screenshots/03-combined-ender-rack-concept.png)

## Load/footprint comparison

No credible material-density metadata was present, so mass and inertia were not invented.

| Assembly | BRep envelope | Modeled solid volume |
|---|---|---:|
| TradRack moving selector, excluding MGN9 and rigid cable-chain treatment | 112.100 × 89.064 × 111.100 mm | 160,727.9 mm³ |
| Removed Ender hotend/fan assembly | 54.024 × 67.791 × 67.791 mm | 52,672.1 mm³ |

The selector is roughly three times the modeled solid volume and has a substantially larger envelope. Volume is not mass, and the TradRack axis will move more slowly than a print hotend, but the CAD does **not** support an assumption that the moving load is equivalent. Weigh the physical selector and calculate acceleration/belt loads before setting motion parameters.

## Physical verification priorities

1. Measure every proposed Ender carriage adapter hole: center coordinates, diameter, counterbore/boss, and usable thread/clearance.
2. Verify the outward carriage face plane, 2.5 mm plate thickness, bends, and local embossments.
3. Verify all three wheel centers, the 40.000/44.721 mm spacing, and eccentric range.
4. Measure the Ender extrusion section, actual cut length, and usable T-slot length between end hardware.
5. Measure the belt centerline, belt-clamp geometry, motor pulley, and idler/tensioner clearance.
6. Measure the actual X endstop trigger point, switch overtravel, homing overshoot, and hard-collision limits.
7. Measure real usable carriage travel with the factory belt and endstop installed; **187 mm is the minimum needed for 12 lanes and 238 mm for 15**.
8. Measure carriage-face-to-V-slot reference distances and wheel contact-plane offsets.
9. Check the TradRack selector entry/output centerline against the first and last physical lane positions.
10. Weigh the complete moving selector and removed Ender hotend/fan assembly; set conservative acceleration only after belt and wheel-load review.

## Deliverable verification

- All three FCStd files were closed, reopened, and recomputed through MCP: **PASS**.
- Required concept groups and `Dimensional_Audit`: **PASS**.
- Reopened object counts: TradRack 1,812; Ender 537; concept 623.
- No null Part features in the reopened documents; targeted interface topology checks passed.
- Existing unrelated FreeCAD documents `Unnamed` and `parametric_l_bracket` remained open and untouched.
- Source archive and STEP hashes remained unchanged after the complete workflow.
- Local RPC remained bound only to `127.0.0.1:9875`.

## File hashes

| Deliverable | SHA-256 |
|---|---|
| `TradRack_R1_reference.FCStd` | `893EC9FDA18AC8F12F0146C73DC632FA9542FCF0BAA3AD97D5BBE908028ED768` |
| `Ender3V2_reference.FCStd` | `894B6FE2D1A605C4C2FBEB6D8400565C818AC563AF3E84669EBAAFA5DE6BBB53` |
| `EnderRack_Concept.FCStd` | `96F41CBEDA633CB7D9129F39E6269E7895752B6C452B4DEE0E06F2B09E5858FD` |
