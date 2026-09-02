# EnderRack 15-Lane Conversion Design Report

> **LEGACY / SUPERSEDED:** The current controlling article is R5. This report is retained as engineering history and must not override `docs/CURRENT_STATE.md` or the current handoff.

> **SUPERSEDED CARRIAGE INTERFACE — PHYSICAL FIT-CHECK FAILED.** Do not fabricate the adapter or continue tensioner redesign from this document's community-CAD carriage coordinates. The digital pipeline reproduced the selected E1–E5 centers correctly, but the pattern does not match the plate on this machine and the selected source cylinders were not all equivalent mounting holes. Preserve the unaffected TradRack and lane-system work. See [`interface-recovery/ENDER_CARRIAGE_INTERFACE_AUDIT.md`](interface-recovery/ENDER_CARRIAGE_INTERFACE_AUDIT.md).

**Status: PROVISIONAL — FIT-CHECK FABRICATION ONLY. DO NOT FABRICATE PRODUCTION PARTS.**

Generated 2026-08-31 in FreeCAD 1.1.3 through the local FreeCAD MCP connection on `127.0.0.1:9875`.

## Outcome

The requested parametric conversion model is implemented. It has a 15-lane target, a 12-lane fallback generated from the same model, editable travel and array parameters, a relieved Ender-carriage adapter, a removable endstop-trigger concept, service-access envelopes, and a separate PLA fit-check derivative exported as STEP and STL.

The interface and parameter pipeline pass. The complete mechanism is **not production-cleared**: exact BRep checks expose a stock-selector/stock-Ender-tensioner conflict over the left-side travel region. This is the first production geometry item to resolve after physical measurement. The rough 270 mm observation supports a 15-lane target but does not prove usable homed travel.

| Item | Result |
|---|---|
| Parametric 15/12/16 lane regeneration | **PASS** |
| Close, reopen, and recompute | **PASS** |
| Adapter topology | **PASS — one valid solid** |
| Fit-check FCStd/STEP/STL | **PASS** |
| Center-position exact collision check | **PASS — zero collisions after declared replacement parts are excluded** |
| Centered 15-lane first extreme | **FAIL — lower selector motor mount vs Ender tensioner; one Ender moving screw also reaches fixed roller hardware at −119 mm** |
| Centered 15-lane last extreme | **PASS in community CAD** |
| Production exports | **NOT CREATED, by design** |
| Production mechanical release | **FAIL / gated by physical verification and left-end redesign** |

## Deliverables

- `EnderRack_15Lane_Design.FCStd` — self-contained parametric design document.
- `EnderRack_Interface_FitCheck.FCStd` — isolated fit-check assembly and manufacturing notes.
- `exports/EnderRack_Interface_FitCheck.step` — fit-check geometry only.
- `exports/EnderRack_Interface_FitCheck.stl` — fit-check geometry only, 960 facets.
- `ENDER_RACK_CAD_AUDIT.md` — original feasibility audit plus design-phase rebaseline.
- `screenshots/07-ender-rack-15-lane-design.png` through `11-interface-fitcheck-part.png` — implementation views.

No production STEP or STL was generated.

## Master parameters

The FreeCAD spreadsheet `Master_Parameters` drives the lane array, travel scenarios, interface placement, adapter thickness, service clearances, and print-fit allowances.

| Parameter | Current value | Role |
|---|---:|---|
| `ActiveLaneCount` | 15 | Change to 12 for fallback or 16 for sensitivity only |
| `LanePitch` | 17.000 mm | Measured stock TradRack pitch |
| `RequiredActiveTravel` | 238.000 mm | `(ActiveLaneCount - 1) × LanePitch` |
| `ProvisionalPhysicalTravel` | 270.000 mm | Rough user measurement; not a verified operating limit |
| `ArrayOffset` | 0.000 mm | Initial visualization only; keep editable until asymmetric end reserves are measured |
| `SelectorYAdjustment` | +8.250 mm | Controlled outward optimization from the audit reference transform |
| `SelectorZAdjustment` | 0.000 mm | Editable; currently preserves the reference filament relationship |
| `FinalTransformY` | +13.552904 mm | Reference Y + controlled adjustment |
| `FinalTransformZ` | −9.384951 mm | Reference Z |
| `AdapterThickness` | 7.726639 mm | Derived from measured mating planes and Y adjustment |
| `M3ClearanceDiameter` | 3.400 mm | Fit-check starting value for a 0.4 mm nozzle process |
| `PrintRadialClearance` | 0.200 mm | Fit-check compensation, to calibrate on the actual printer |

Changing `ActiveLaneCount` to 12 regenerates 12 lane instances at the same pitch. The verification run also exercised 16 lanes and changed travel to 268/272 mm and selector Y to +8.750 mm; derived travel, first/last centers, adapter thickness, and geometry updated and then returned to the 15-lane baseline.

## Lane scenarios

| Lanes | First-to-last centers | Gross remainder within rough 270 mm | Design status |
|---:|---:|---:|---|
| 12 | 187 mm | 83 mm | Fallback after the same left-end tensioner issue is resolved |
| 15 | 238 mm | 32 mm | Primary target; sensible but physically unverified |
| 16 | 255 mm | 15 mm | Sensitivity only; not released because endstop/hardware reserve is too small |
| 17 | 272 mm | −2 mm | Does not fit the rough measured center travel |

The stock lane/module mounting geometry measured in the audit can pack 19 positions. Travel and end packaging remain the limiting constraints. Final `ArrayOffset` must maximize the smaller of the measured switch-side and far-side safe clearances; centering is not a release assumption.

## Implemented interface

The implemented transform is:

`T_EnderCarriage_From_TradRackSelector = translation(0.000, +13.552904, −9.384951 mm) × rotation(0°, 0°, 0°)`

It retains parallel travel axes and parallel mating planes while moving the selector +8.250 mm outward from the original reference alignment. This places the official module mounting-hole Y datum within 0.250 mm of the measured Ender lower-slot centerline.

The adapter is an L-relieved, parametric one-piece fit-check solid:

- bounding box: **62.000 × 7.726639 × 36.000 mm**;
- exact BRep volume: **14,471.748 mm³**;
- five measured Ender plate hole checks;
- three usable stock selector M3 interface locations;
- three captive-nut pockets;
- localized NEMA motor and cable-cover reliefs;
- a 3.2 mm minimum structural back wall at the motor relief;
- service-access cylinders representing fastener approach, not invented tool models.

The lower-left stock selector fastener is intentionally unavailable inside the motor-relief zone. Two previously colliding selector fasteners are classified for replacement. Hole authority remains provisional until the physical Ender plate is measured.

![Adapter interface](screenshots/08-adapter-interface-closeup.png)

## Collision results and disposition

The exact checks used component BReps rather than only bounding-box estimates. Intentional visualization envelopes were excluded.

| Pose | Translation | Exact result |
|---|---:|---|
| Center | 0.0 mm | 0 collisions |
| 12-lane first, centered | −93.5 mm | Selector lower motor mount intersects Ender tensioner housing |
| 12-lane last, centered | +93.5 mm | 0 collisions |
| 15-lane first, centered | −119.0 mm | Selector lower motor mount intersects Ender tensioner; moving Ender M5 screw reaches fixed Z-roller plate |
| 15-lane last, centered | +119.0 mm | 0 collisions |
| 16-lane first, centered | −127.5 mm | Multiple end-hardware collisions |
| 16-lane last, centered | +127.5 mm | Adjustable trigger begins intersecting the gear enclosure |

Pose probes found that shifting the selector approximately 15 mm farther outward than the implemented +8.250 mm adjustment clears the selector/tensioner collision at a candidate 15-lane first position near −112.5 mm. That larger stand-off was deliberately **not** adopted: it is not the approved small optimization, it would increase the adapter and overturn the near-slot module mounting relationship, and it should be compared against a measured low-profile Ender tensioner solution first.

The current production-design branch therefore needs one of these evidence-backed resolutions:

1. measure and design a low-profile Ender X tensioner that preserves belt centerline and adjustment; or
2. authorize a larger selector stand-off plus explicit lane-module mounting brackets; or
3. reduce/reposition the operating lane window after accurate travel and obstruction measurements.

## Component change classification

### Unchanged

- TradRack filament drive core, NEMA motor, servo mechanism, filament sensor, and entry/output geometry;
- lane-module bodies, bearings, and 17 mm pitch;
- most selector printed structure and hardware;
- Ender X extrusion, V-wheel carriage, motor-side hardware, and belt path reference.

### Repositioned only

- complete selector reference and lane bank through the named parametric transform;
- lane array along X through `ArrayOffset` and `ActiveLaneCount`;
- endstop trigger position after physical switch measurement;
- wiring flex envelope after harness routing is known.

### Replacement required

- MGN9 rail and carriage, replaced by the Ender V-wheel stage and adapter;
- two selector interface fasteners identified in the feasibility audit;
- stock TradRack cable-chain anchor (`Part__Feature405`), because its mounting form intersects an Ender M5 wheel screw;
- a left-end packaging component: provisionally the Ender tensioner housing, unless a later authorized stand-off solution proves preferable.

### Possibly unnecessary

- stock TradRack 280 mm extrusion if the lane modules are mounted to the Ender extrusion or a shared replacement member;
- original MGN9 rail stop and K3 mounting brackets;
- rigid cable chain if a lighter verified flex harness is used.

## Fabrication guidance

The exported part is for **interface fit checking only**.

- Fit-check material: PLA, 0.4 mm nozzle.
- Production adapter baseline after release: PETG minimum; ABS/ASA acceptable.
- Do not use the current PLA fit-check part as a production motion component.
- Verify all five Ender hole locations, selector fastener access, captive-nut fit, plate-face seating, motor relief, and cable-cover relief before editing the production design.
- Do not drill or permanently modify the Ender carriage from these community-CAD coordinates.

## Physical and dynamic release gates

1. Measure from the same carriage center hole at **X switch just clicked** to the **furthest safe opposite position**, without forcing the carriage. Record the two endpoint coordinates separately; ±2 mm is sufficient for the current lane decision.
2. Measure the stock tensioner housing, adjustment knob, Ender moving screw/roller plate, belt centerline, and usable clearance around the proposed first lane.
3. Verify carriage adapter holes, plate face, thickness, bosses/counterbores, and accessible fastener approach.
4. Verify lane-module mounting datums and the selector filament centerline after choosing the left-end packaging solution.
5. Weigh the complete moving selector. No density-derived mass was invented from the STEP files.
6. Verify harness bend/flex space throughout travel; the present wiring volume is provisional.
7. After a fit-check passes, home and address the first, middle, and last lane repeatedly. Characterize positional repeatability before calling the V-wheel stage production-ready; set the acceptance tolerance from the real TradRack filament-entry geometry rather than inventing one now.
8. Establish safe homing speed, switch overtravel, overshoot reserve, belt tension, and acceleration only after the physical checks.

## Verification record

- Design document reopened and recomputed: **PASS**.
- Groups, aliases, placements, arrays, and copied geometry persisted: **PASS**.
- Adapter: **one valid solid**, 14,471.748 mm³.
- Fit-check STEP: **one valid solid**.
- Fit-check STL: **solid mesh**, 960 facets, mesh volume 14,476.395 mm³.
- No production exports present: **PASS**.
- Source hashes unchanged: **PASS**.
- RPC used local loopback only: **PASS**.

| File | SHA-256 |
|---|---|
| `EnderRack_15Lane_Design.FCStd` | `5548FD411AB25CAA5D49DA87254DBB6143FCBED0504B2039C3418DE7E0B6E1D4` |
| `EnderRack_Interface_FitCheck.FCStd` | `6E27DB212DEC36AFD9EDEE3BF8660E55BE5FCD03E1C8D9B63AFBD4966D62D00E` |
| `exports/EnderRack_Interface_FitCheck.step` | `DFB476A0BD1112BF8C5DE84C189DD2B0EF29DAF8E8B0E3CC908E68EF272F5F87` |
| `exports/EnderRack_Interface_FitCheck.stl` | `6F96E7328E8FC8571B804113EB810008C07098645E74A027D379F70089975B3F` |

The source archive/STEP SHA-256 values remain `BE7646…71E8`, `19459C…BDB3`, and `D81BDE…B5D0`, matching the feasibility audit.

![Complete parametric design](screenshots/07-ender-rack-15-lane-design.png)

![Lane array](screenshots/09-parametric-15-lane-array.png)

![First 15-lane extreme](screenshots/10-15-lane-first-extreme.png)

![Last 15-lane extreme](screenshots/10-15-lane-last-extreme.png)
