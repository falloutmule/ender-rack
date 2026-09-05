# EnderRack

EnderRack is an experimental high-lane-count adaptation of the [Annex Engineering TradRack](https://github.com/Annex-Engineering/TradRack) selector architecture to the complete X-axis motion system of an original/older Creality Ender-3-family donor printer.

The intended architecture retains the Ender X extrusion, V-wheel carriage, belt, motor, idler/tensioner, and endstop while replacing the stock TradRack MGN9 selector stage with a custom carriage-to-selector interface. The primary target is 15 lanes at the stock 17 mm TradRack pitch; 12 lanes remains the fallback generated from the same future parametric model.

## Current status

**Experimental. No production-ready release exists.**

The current article is **R7_ARCHITECTURE_V2_Candidate_001**. It has been printed and physically seats on the intact Ender carriage at the observed scope; a recurring boss-clearance overhang print defect did not prevent fit. No TradRack selector has been built yet, so full R7 physical PASS is **not** complete.

Next: [print and assemble the exact stock moving selector](docs/STOCK_SELECTOR_BUILD.md), then finish the R7 physical test. Production work and the 238 mm sweep remain gated. Earlier broad master/reproducibility claims require re-audit under the upgraded FreeCAD skill before production release.

Start with [CURRENT_STATE.md](docs/CURRENT_STATE.md), then read the complete [engineering handoff](docs/ENDER_RACK_HANDOFF.md).

## Validation approach

The project uses a physical-validation-gated workflow:

`reference CAD -> digital correlation -> cheap coupon -> physical PASS -> dependent geometry`

The earlier Ender-3 V2 reference failed this workflow and is archived as rejected evidence. The official original Ender-3 E-plate interface subsequently passed the R2 physical coupon test for the specific features exercised by that coupon.

## Upstream attribution

- [Creality3DPrinting/Ender-3](https://github.com/Creality3DPrinting/Ender-3)
- [Annex-Engineering/TradRack](https://github.com/Annex-Engineering/TradRack)

See [SOURCES.md](sources/SOURCES.md) and [LICENSE_NOTES.md](sources/LICENSE_NOTES.md). Complete upstream archives and assemblies are intentionally not vendored here. No EnderRack-wide license has been selected.
