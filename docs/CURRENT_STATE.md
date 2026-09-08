# EnderRack current state

Updated 2026-09-07. **Current article: R7_ARCHITECTURE_V2_Candidate_001. Printed; scoped carriage fit PASS; full R7 physical PASS NOT YET. Controlling selector remains stock TradRack R1.**

## Physical state — owner report

The Ender donor was NEVER disassembled. Original Ender X-axis hardware remains assembled/in place. The exact R7 V2 print seats on the real Ender carriage and visually aligns correctly. The boss-clearance unsupported-overhang print defect recurred but did not prevent observed seating. No physical TradRack selector has been built yet.

Correct carriage face, seating, exercised carriage-hole relationship, visible wheel-fastener relationship, and boss-clearance seating function PASS only at the observed scope. Selector fit, belt/clamp dynamic clearance, rocking/translation/rotation and complete physical validation are NOT TESTED. See [scoped physical report](reports/R7_V2_PHYSICAL_CARRIAGE_FIT.md).

## Recorded digital state before printing

Verifier v0.2: 19/19 checks PASS. The candidate's complete installed selector check reported no positive-volume interference among evaluated valid geometry; invalid source gear remained UNVERIFIED. Cable-cover nominal clearance 2.950 mm; left body 2.211 mm; minimum window-to-pilot material 0.975 mm. These are recorded CAD results, not physical measurements or strength proof. Stand-off +15.0 mm remains a candidate relationship.

## Audit caveat

Installed upgraded FreeCAD skill: commit `7c26a143d2a6e4318724b96cc71c297f7424efa0`. Earlier broad master-context/reproducibility claims preceded discovery of stale embedded context metadata, 48 unreconciled shape occurrences, hidden live-session generator dependencies and ineffective declared parameters. Those claims require re-audit before production release. The audit caveat does not erase observed physical carriage fit or promote invalid geometry to clear. No whole-master re-audit was performed for this selector-build task.

## Immediate next action

Build the exact [stock moving selector](STOCK_SELECTOR_BUILD.md), then finish R7's physical test. The [Binky/EREC comparison](MODDED_SELECTOR_COMPARISON.md) did not establish an evidence-complete modded R7 relationship: the primary Fusion assembly cannot be authoritatively decoded in FreeCAD, and the STEP fallback contains an invalid encoder-left body overlapping the R7 region. Stock remains controlling; R7 remains frozen. Measure the spare Ender stepper and both mirrored BMG-clone internals before buying replacements.

R7 architecture/frame, four selector axes and +15 mm candidate placement remain frozen. R5 and its 22.25 mm relationship are retired. R6/R6R1 geometries are rejected. R6R2 DIGITAL_OBJECT PASS; PHYSICAL TEST WAIVED BY OWNER, NOT A PHYSICAL PASS. Historical solids are evidence, not construction inputs.

## Downstream gate

Full R7 physical PASS precedes production adapter and full 238 mm selector sweep. Fifteen lanes at 17 mm pitch remains the goal; twelve lanes the fallback. First/middle/last master positions were context views, not a validated sweep. No redesign, slicing, printing command, production work or sweep was performed in this documentation task.
