# EnderRack

EnderRack is an experimental high-lane-count adaptation of the [Annex Engineering TradRack](https://github.com/Annex-Engineering/TradRack) selector architecture to the complete X-axis motion system of an original/older Creality Ender-3-family donor printer.

The intended architecture retains the Ender X extrusion, V-wheel carriage, belt, motor, idler/tensioner, and endstop while replacing the stock TradRack MGN9 selector stage with a custom carriage-to-selector interface. The primary target is 15 lanes at the stock 17 mm TradRack pitch; 12 lanes remains the fallback generated from the same future parametric model.

## Current status

**Experimental. No production-ready release exists.**

The controlling CAD article is the R5 secondary selector-interface coupon. It has passed digital topology, export-fidelity, and static clearance checks, but its current Orca G-code is diagnostic only: it used an Ender-3 V2 preset and carries a material-temperature warning. The immediate prerequisite is to select and verify the correct original Ender-3-family 0.4 mm printer profile and approved PLA temperatures, then re-slice R5.

After re-slicing, R5 must pass a physical static fit test with the real TradRack selector. The complete 238 mm motion sweep, tensioner resolution, and production adapter remain blocked until that physical gate passes.

Start with [CURRENT_STATE.md](docs/CURRENT_STATE.md), then read the complete [engineering handoff](docs/ENDER_RACK_HANDOFF.md).

## Validation approach

The project uses a physical-validation-gated workflow:

`reference CAD -> digital correlation -> cheap coupon -> physical PASS -> dependent geometry`

The earlier Ender-3 V2 reference failed this workflow and is archived as rejected evidence. The official original Ender-3 E-plate interface subsequently passed the R2 physical coupon test for the specific features exercised by that coupon.

## Upstream attribution

- [Creality3DPrinting/Ender-3](https://github.com/Creality3DPrinting/Ender-3)
- [Annex-Engineering/TradRack](https://github.com/Annex-Engineering/TradRack)

See [SOURCES.md](sources/SOURCES.md) and [LICENSE_NOTES.md](sources/LICENSE_NOTES.md). Complete upstream archives and assemblies are intentionally not vendored here. No EnderRack-wide license has been selected.

