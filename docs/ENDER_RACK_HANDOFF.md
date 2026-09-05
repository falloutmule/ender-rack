# EnderRack engineering handoff

Read [CURRENT_STATE.md](CURRENT_STATE.md), [R7 V2 physical report](reports/R7_V2_PHYSICAL_CARRIAGE_FIT.md), then [STOCK_SELECTOR_BUILD.md](STOCK_SELECTOR_BUILD.md).

## Controlling facts

- Original/older Ender-3-family mechanical donor: intact X-axis, never disassembled. Aquila is the coupon print machine, not the mechanical reference.
- Official Creality E-plate and scoped R2 physical interface evidence establish the carriage interface. Preserve its established physical face correlation.
- ENDER_INTERFACE v1 and authenticated stock TradRack selector interface are the inputs; historical coupon solids are evidence only.
- R7_ARCHITECTURE_V2_Candidate_001 has been printed and fits the carriage at the owner-observed scope. Its recurring boss-clearance overhang defect is recorded, not redesigned here.
- No stock selector exists physically yet. Build the resolved 9 mm C-cart / 10x10-right / Micro-Fit / FT1117M moving selector, excluding the replaced stock MGN motion stage.
- +15.0 mm selector stand-off is candidate, not measured/validated. Full R7 physical PASS has not occurred.

## Preserve architecture and evidence

R7 V2 has two named exterior-open carriage-access reliefs and one main load path. Do not silently change topology, pilots, orientation, base or stand-off. No historical coupon contours as construction input. The 5 mm clearance preference is not a fabricated physical requirement; the 0.975 mm reported minimum window-to-pilot material is not a strength certification.

The prior 19/19 v0.2 result and valid-component clearance findings are historical digital evidence. Invalid source gear remains UNVERIFIED. Upgraded skill `7c26a143d2a6e4318724b96cc71c297f7424efa0` identified stale master metadata, 48 unreconciled occurrences, live-session dependencies and ineffective parameters. Re-audit broad reproducibility/whole-assembly claims before production, without erasing the scoped physical result.

## Next physical sequence

Assemble the stock moving selector from the build sheet. Tighten R7-to-Ender fasteners before installing the selector. Determine safe selector screw engagement; finger-snug only. Record all R7 physical checks, including actual stand-off, motion of the mounted joint and real hardware/tool clearances. No powered commissioning yet. R7 physical PASS unlocks production adapter and 238 mm sweep; context views do not unlock them.

## Repository handling

Always read actual HEAD and dirty state; do not reset to a remembered baseline. The 2026-09-04 documentation update was made in a clean current-remote clone to preserve pre-existing verifier/tool edits in the original dirty checkout. See the physical report for baseline and change scope. Upstream TradRack remains pinned to `f89dc0b115adfc49195d782c5d7ecd348a574891`; do not casually update CAD or variants.
