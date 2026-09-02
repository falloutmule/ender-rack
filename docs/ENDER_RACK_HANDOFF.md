# EnderRack engineering handoff

## Read this first

**CURRENT CONTROLLING ARTICLE: R5 secondary selector-interface coupon.**

Older V-notch instructions are superseded. R5 uses the motor-side engraved cross and the opposite reinforced wheel-edge as the tensioner/idler side. Do not reconstruct or reuse the rejected Ender-3 V2 interface work.

## Project objective

EnderRack is a high-lane-count TradRack MMU conversion that reuses the complete X-axis linear-motion system of an original/older Creality Ender-3-family donor instead of the stock TradRack MGN9 selector stage.

Target architecture:

- Ender X extrusion and V-wheel carriage;
- factory belt, motor, idler/tensioner, and endstop system;
- custom carriage-to-TradRack selector interface;
- mostly stock TradRack selector and scalable lane bank;
- Klipper/Happy Hare and donor electronics where practical.

Primary target: 15 lanes. Fallback: 12 lanes. TradRack pitch: 17 mm. Fifteen lanes span 238 mm; twelve span 187 mm. Do not pursue 16 lanes unless explicitly reopened. Seventeen lanes is excluded on the approximately 270 mm measured gantry.

## Machine and source correction

The donor was initially misidentified as an Ender-3 V2. Its display may be upgraded and must not be used to infer mechanical identity. The community `Creality-Ender3-V2-rev4.STEP` was therefore the wrong fabricated-fit reference. All V2-derived carriage coordinates, transforms, adapters, and collision conclusions are archived and superseded.

The controlling donor CAD is the official Creality Ender-3 repository at commit `88c7758cea9d0d00a54fdb238bedb3b33425f409`. `Ender3.STEP` imported through local FreeCAD MCP with 1,243 objects and passed topology, placement, save/reopen, and recompute checks. The official carriage component is `E plate`.

Correct interpretation:

- physical plate and official E plate correspond when the rear face and correct 180-degree in-plane orientation are used;
- official upper-wheel spacing is 40.000 mm;
- gold `Copper cover002/003` objects are separate belt hardware;
- the two 14 mm-spaced hotend bosses are integral E-plate topology;
- the corresponding M3x16 screws are separate objects in `Sprinkler_assembly`.

## R2 physical carriage reference

The earlier V2 coupon failed and remains rejected evidence. The official Ender-3 R2 coupon physically fit the real carriage and was reported as fitting perfectly.

R2 validates only:

- the physically exercised hole pattern and orientation;
- the real steel seating face;
- the boss-clearance relationship;
- R2 V-notch = tensioner/idler and R2 cross = motor side.

It does not validate every E-plate surface, belt datum, or wheel-stack depth. Its two pockets are diameter 5.5 mm by 5.2 mm deep. The earlier 5 x 5 mm values are successful nominal coupon inputs, not independently measured boss dimensions. The bosses are clearance features rather than locating datums.

Canonical R2 files:

- `cad/fit-checks/Ender3_Official_Carriage_FitCheck_R2.FCStd`;
- `exports/fit-checks/Ender3_Official_Carriage_FitCheck_R2.step`;
- `exports/fit-checks/Ender3_Official_Carriage_FitCheck_R2.stl`.

## Physical evidence retained

| Measurement | Value | Confidence / qualification |
|---|---:|---|
| X-carriage total safe travel | approximately 270 mm | medium-high; physical, provisional |
| Travel midpoint | approximately 135 mm | derived from physical travel observation |
| Stock X tensioner length | approximately 45 mm | low |
| Tensioner protrusion | approximately 7 mm | low; datum unresolved |
| Belt centerline on 20 mm extrusion | approximately 10 mm | low; datum must be restated |
| Tensioner pulley center from extrusion end | approximately 10 mm | low-medium |
| TradRack lane pitch | 17 mm | high |

At 270 mm gross travel, 15 lanes leave approximately 32 mm total gross remainder. Twelve leave approximately 83 mm. Sixteen leave only approximately 15 mm and are intentionally not targeted. Final lane placement must use verified asymmetric end reserves rather than forced centering.

## TradRack architecture retained

Preserve the official TradRack R1 reference, filament-drive core, selector servo, filament sensor/output path, lane geometry, 17 mm pitch, Happy Hare/Klipper strategy, and shared 15/12-lane parametric intent. The desired result remains removal of the MGN9 rail/carriage while keeping the selector essentially unchanged, subject to the current interface test.

## Current R5 coordinate and interface state

Frame:

- origin at the motor-side upper-wheel axis projected onto the steel contact face;
- +X toward tensioner/idler;
- +Y outward toward selector;
- +Z machine-up;
- `Y=0` steel contact face;
- `Y=22.25 mm` selector-facing face.

Static transform:

`T_EnderCarriage_From_TradRackSelector = translation(+15.000, +22.250, -20.300 mm) x rotation(0, 0, 0 degrees)`

R5 properties:

- 61.500 x 22.250 x 40.550 mm bounding box;
- one valid solid;
- 5 mm lateral and lower material around both wheel reliefs;
- two full-height triangular selector-block gussets;
- four blind diameter 2.7 x 6.5 mm temporary M3 pilots;
- cross = motor side;
- opposite reinforced edge = tensioner/idler side;
- R2 V-notch removed from load-bearing geometry.

Digital checks:

- selector/coupon, wheel-envelope, and conservative-belt intersections: 0 mm3;
- R2 contact-layer geometry preserved;
- STEP fidelity: PASS;
- STL fidelity: PASS;
- save/reopen/recompute: PASS;
- conservative selector-to-belt minimum: 0.867 mm.

Record the result as `STATIC GEOMETRY PASS / BELT-CLEARANCE TARGET SHORT BY 0.133 MM / PHYSICAL CONFIRMATION REQUIRED`. Do not redesign solely because the conservative model reports 0.867 mm.

Canonical R5 files:

- `cad/working/EnderRack_Selector_Interface_Coupon_R5.FCStd`;
- `exports/fit-checks/EnderRack_Selector_Interface_Coupon_R5.step`;
- `exports/fit-checks/EnderRack_Selector_Interface_Coupon_R5.stl`.

## Immediate prerequisite: correct slicing

The current live-Orca R5 slice proves the model can be loaded, oriented, placed, and sliced, but it is not released for printing. It used `Creality Ender-3 V2 0.4 nozzle` and has level-3 warning `1000C001 bed_temperature_too_high_than_filament`. The donor is not mechanically a V2.

Before printing:

1. Use the isolated MCP-enabled Orca installation already established for this project.
2. Select and verify the exact built-in/local original Ender-3-family 0.4 mm printer profile. If unavailable, stop and show near matches.
3. Use the verified PLA profile and obtain an approved/spool-specific bed temperature; do not guess.
4. Load only the canonical R5 STL at 100%.
5. Put the broad steel-contact face on the bed and visually confirm orientation and first-layer contact.
6. Retain the established process intent: 0.20 mm layers, 3 walls, 4 top, 3 bottom, 15% crosshatch, supports disabled, subject to verification in the matching profile.
7. Slice again and require no unresolved safety/geometry warnings before marking it ready for the physical coupon print.

The existing diagnostic G-code must not be sent to a printer.

## Physical R5 selector test

After an approved re-slice, print the R5 STL in PLA at 100%. Mount it to the validated E plate with the cross on the motor side and reinforced opposite edge on the tensioner/idler side. Support the real stock TradRack selector while attaching it finger-snug.

Check:

1. Coupon fully seats on the E plate.
2. Selector holes align without force or modification.
3. Selector reaches the intended stand-off and orientation.
4. Interface has no appreciable rocking, translation, or rotation.
5. Wheel/eccentric hardware and belt clamp remain clear and serviceable.
6. Actual belt remains clear through its normal small movement.
7. Fasteners and tools can be installed and removed.
8. Gentle twist, inward/outward push, vertical rock, and light hand load do not expose concerning interface movement or flex.

If there is belt or hardware contact, identify and measure the contact location before changing stand-off or geometry.

## Work blocked until R5 physical PASS

Do not:

- run or claim the complete 238 mm selector sweep;
- design the production adapter;
- redesign the tensioner;
- generate the complete 15-lane structure or production exports;
- add stand-off to solve hypothetical end-of-travel collisions;
- revive V2-derived transforms or collision conclusions.

## After physical PASS

1. Promote the static transform as physically validated for the exercised interface.
2. Build the full adapter from that interface.
3. Reconstruct the complete selector motion model with the correct Ender-3 carriage.
4. Run the complete 238 mm 15-lane sweep.
5. Reintroduce the physical tensioner envelope and verify actual end hardware.
6. Resolve collisions in order: stock tensioner, local selector/mount relief, low-profile tensioner preserving belt centerline, then larger stand-off only if necessary.
7. Re-evaluate cable routing and cable-chain anchor.
8. Test first/middle/last-lane repeatability on the real V-wheel stage before production release.
9. Keep 12-lane generation available from the same future master model.

## Electronics concept

A spare Creality board may become a dedicated Klipper MMU MCU only after its physical board/version marking and usable pins are confirmed. Do not infer board revision from the donor model or display. Consider a separately rated 5 V supply/buck for servo power rather than assuming the board regulator can carry servo current.

## Source-of-truth rule

For fabricated interfaces:

`reference CAD -> digital correlation -> simplest coupon -> physical PASS -> dependent geometry`

A reference is controlling only for the features actually validated. Failed coupons are evidence; they are not permission to apply arbitrary offsets.

