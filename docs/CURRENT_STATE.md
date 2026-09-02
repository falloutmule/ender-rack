# EnderRack current state

**CURRENT CONTROLLING ARTICLE: R5 secondary selector-interface coupon.**

Older V-notch instructions are superseded. R5 uses:

- engraved cross = motor side;
- opposite reinforced wheel-edge side = tensioner/idler side;
- steel-contact face at `Y=0`;
- selector-facing face at `Y=22.25 mm`.

## Current transform

`T_EnderCarriage_From_TradRackSelector`

- translation: `X +15.000 mm`, `Y +22.250 mm`, `Z -20.300 mm`;
- roll/pitch/yaw: `0 / 0 / 0 degrees`;
- +X toward tensioner/idler, +Y outward, +Z machine-up.

## Digital status

- one valid printable solid: PASS;
- FCStd/STEP/STL fidelity: PASS;
- selector, wheel-envelope, and conservative-belt intersections: 0 mm3;
- minimum conservative selector-to-belt clearance: `0.867 mm`;
- fabrication state: **PROVISIONAL - STATIC FIT-CHECK ONLY**.

## Immediate prerequisite

The existing R5 G-code is diagnostic only. It used `Creality Ender-3 V2 0.4 nozzle` and has Orca warning `1000C001 bed_temperature_too_high_than_filament`.

Select and verify an exact original Ender-3-family 0.4 mm profile and an approved/spool-specific PLA temperature, then re-slice R5 at 100% scale. Do not guess missing profile or temperature values.

## Physical gate

After a warning-free approved slice, print R5 and mount the real stock TradRack selector finger-snug. Check seating, hole alignment, rotation/translation/rocking, wheel and belt access, fastener access, belt clearance, and light hand-load stiffness.

## Blocked until physical PASS

- complete 238 mm 15-lane sweep;
- production adapter;
- tensioner redesign;
- complete lane structure and production exports.

Full context: [ENDER_RACK_HANDOFF.md](ENDER_RACK_HANDOFF.md).

