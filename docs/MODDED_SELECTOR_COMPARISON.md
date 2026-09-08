# Modded selector comparison

Updated 2026-09-07. **Selected build: authenticated stock TradRack R1 moving selector.** The Binky and EREC/cutter variants remain useful future options, but neither has an evidence-complete R7 compatibility result. R7 geometry was not changed.

Repository baseline before this comparison update: `875ec737eb1b558d64b7c11aca0a0677c10a04d2`, clean working tree. History was not reset or rewritten.

## Decision

| Option | Evidence | R7 result | Decision |
|---|---|---|---|
| A. Stock TradRack R1 | Pinned upstream default STEP, pinned STLs, official BOM/manual; existing complete-selector R7 check | DIGITALLY COMPATIBLE at the recorded candidate relationship; invalid stock gear remains UNVERIFIED; physical selector test outstanding | **BUILD THIS** |
| B. R1 + Binky | Printables 963410 complete STEP reference; valid Binky bodies evaluated in the stock-R1 frame | **UNVERIFIED**: Binky rack clears R7 by 3.030 mm and valid encoder-right body by 1.874 mm, but encoder-left is an invalid source BRep whose bounding box overlaps the R7 region | Do not print as the controlling selector |
| C. R1 + Binky + EREC cutter | Printables 1385926 editable Fusion source and physical-build evidence; 963410 STEP reference; 985791 STL cutter evidence | **UNVERIFIED**: primary Fusion archive cannot be decoded into authoritative BReps/placements by the installed FreeCAD toolchain; fallback STEP retains the invalid overlapping encoder-left body. Valid cutter-reference bodies did not positively intersect R7; one modeled MG996R servo body is only 0.172 mm clear | Do not print as the controlling selector |

This is not a physical PASS for any selector. The existing R7 carriage-side fit remains scoped physical evidence only.

## Sources inspected

- Official authority: Annex Engineering TradRack commit `f89dc0b115adfc49195d782c5d7ecd348a574891`, `CAD/Trad_Rack_R1_2024-03-04_STEP.7z` -> `trad_rack_(default).STEP`.
- Primary mod candidate: [TradRack Binky+EREC Integration](https://www.printables.com/model/1385926-tradrack-binkyerec-integration-trianglelabs-partne), RedHeadnDead, CC BY, published 2026-04-26. It supplies 17 STL files and `Tr-B-EREC.f3d` (`a8720d880db6ff864ebedba0aa5a94ab2e2b68de9ed46b5c23b8c72be6046d12`). The author reports a physical build and describes a stronger Binky mount, removable Binky/EREC, a larger selector servo, and an inverted EREC gear assembly.
- Assembly-CAD reference: [TradRack MMU + Binky + Filament Cutter + User Mods CAD Model](https://www.printables.com/model/963410-tradrack-mmu-binky-filament-cutter-user-mods-cad-m), BakedBean3D, GPL-2.0. It supplies Binky-only and Binky+EREC STEP assemblies. Its author explicitly says the modeled Binky integration was not printed or used.
- Cutter implementation evidence: [TradRack Encoder + Cutter Mod](https://www.printables.com/model/985791-tradrack-encoder-cutter-mod), Pham Tuan, GPL-2.0. It supplies STL variants, not an editable/assembled source; the page identifies a retained gate switch, V/623 encoder options, EREC integration, and changed cable position.
- Binky upstream: Marc Neuhaus's `EnragedRabbitProject/usermods/Binky`. Binky replaces the optical encoder with an EE-SX398-based PCB and filtered slotted wheel, using a BMG idler gear, its needle bearings and 3 x 20 mm pin. It remains mounted on the moving selector and adds a three-wire encoder connection.
- Cutter upstream: KevinAkaSam/BioKeks EREC Beta 7.0. It is a servo-actuated, selector-mounted inline cutter behind the encoder. A scalpel/Exacto blade sits on a swinging arm carrying the ECAS fitting; opening permits tip feed, closing cuts, and the separated tip falls out. Happy Hare requires its EREC add-on configuration and cutter action; firmware commissioning is later work.

The repository [source manifest](reports/MODDED_SELECTOR_SOURCE_MANIFEST.json) anchors the official files and principal assemblies. The complete 44-file Printables inventory, including every STL hash and file ID, is preserved in external scratch as `source_provenance_manifest.json` beside the downloaded sources.

## Frame and R7 check

The mod reference was correlated to stock R1 first, then carried through the existing stock-R1-to-E relationship. No independent Ender face was inferred.

`T_E<-MOD`, millimetres, column-vector convention:

```text
[ 1  0  0  -20.375000000 ]
[ 0  0  1   25.022256770 ]
[ 0 -1  0  -52.031656654 ]
[ 0  0  0    1.000000000 ]
```

The rotation is orthogonal, right-handed, determinant +1, unit scale and no shear. It maps the modded 9 mm/C-cart middle-carriage reference back to the authenticated stock selector frame; R7 remains at +15.0 mm candidate stand-off with its four frozen pilot axes.

### Numeric evidence

| Reference occurrence | Source validity | R7 intersection | R7 distance | Disposition |
|---|---:|---:|---:|---|
| `BinkyRack wgate switch encoder mount (Exerqtor_82339)` | valid | 0.000 mm3 | 3.030 mm | clear in this reference placement |
| `Encoder Right (2)(Mirror)` | valid | 0.000 mm3 | 1.874 mm | clear, small nominal margin |
| `Encoder Left (2)(Mirror)` | **invalid** | not evaluated as zero | overlapping bounding region | **UNVERIFIED** |
| EREC/cutter valid bodies | valid | no positive-volume R7 intersection found | nonblocking except servo below | reference only |
| `servoMotorMG996R (1)(Mirror)` | valid | 0.000 mm3 | 0.172 mm | technically clear, not a practical validated margin |

Stock MGN carriage, rail screws and lane-module occurrences present in the reference STEP were excluded because EnderRack replaces that translation system. They are not selector collisions. Unchanged stock selector geometry uses the authenticated official R1 source rather than invalid duplicate imports from the community STEP.

The result is not promoted to `MODDED SELECTOR / R7 INTERFACE DIGITALLY COMPATIBLE`: the invalid encoder-left source body overlaps the only region where a collision would matter. Kernel/source failure is UNVERIFIED, never zero.

## Part replacement map

The primary mod's native assembly membership cannot be recovered from the F3D without Autodesk ShapeManager support. Filename-only mappings below are intentionally not promoted to authoritative replacements.

| Official R1 part | Primary mod evidence | Status |
|---|---|---|
| cable cover | `[a] Tr-B-EREC_Cable Chain Mount.stl`; no stock-named cable cover supplied | replacement relationship **UNRESOLVED** |
| carriage left | `Tr-B-EREC_Carriage - Left.stl`, `Carriage - Left Arm.stl` | MODIFIED/REPLACED family; exact occurrence split UNRESOLVED |
| carriage middle, 9 mm/C-cart | `Tr-B-EREC_Carriage.stl` | likely modified integration body, but pilot/mating correspondence **UNVERIFIED** |
| carriage right, 10x10 | `Carriage - Right Arm.stl`, cable-chain mount | MODIFIED/REPLACED family; exact 10x10 correspondence **UNVERIFIED** |
| Micro-Fit holder | no unambiguous matching mod file | UNRESOLVED; do not infer removal |
| servo horn | `[a] Tr-B-EREC_Servo Horn.stl` plus selector servo spacers/cage | REPLACED for larger-servo design |
| arm; gear casings left/right; motor plate; NEMA17 spacer; tensioner collar | no replacements supplied by name | stock carry-over is plausible from author instructions, but assembly membership UNVERIFIED |
| filament-drive NEMA17 and conventional BMG drive | author says follow TradRack BOM; no replacement motor-drive file | unchanged function; exact hardware envelope UNVERIFIED |
| Binky encoder | encoder left/right, Binky PCB/slotted wheel implied by source description | ADDED on moving selector |
| EREC cutter | cutter arm, servo gear/rig/cage, tip catcher | ADDED inline cutter architecture |

## What Binky adds

Binky provides direct filament-motion feedback with a slotted wheel and filtered optical PCB. It adds encoder wiring and changes the moving-selector/cable envelope. The standard Binky mechanism uses BMG-style idler components, so parts from the two mirrored BMG clones are worth measuring. Housing handedness alone does not disqualify internals. Binky is not selected yet because the complete R7 relationship remains UNVERIFIED.

## What the cutter adds

EREC Beta 7 adds a second servo, printed cutter/encoder support, servo gear, swinging ECAS cutter arm, blade, fasteners/inserts and a tip catcher. It adds a blade consumable, debris path, cable load and Happy Hare add-on configuration. It is not required to establish initial stock EnderRack operation, and its integration changes the selector envelope checked by R7.

## Build selection and next action

Print and build the exact stock R1 selector in [STOCK_SELECTOR_BUILD.md](STOCK_SELECTOR_BUILD.md). First measure the spare Ender stepper and both mirrored BMG clones using the reuse checklist in that document; do not buy the filament-drive motor or genuine Bondtech internals until those measurements are compared. Mount the completed stock selector finger-snug to the already printed R7 and finish the physical R7 checklist before selecting Binky, cutter, production adapter or the 238 mm sweep.

## External inspection artifacts

The source downloads, complete provenance manifest, comparison FCStd and four rendered views are staged outside the Git tree at:

`C:/Users/fallo/Documents/Codex/2026-09-02/files-pasted-by-the-user-continue/EnderRack-Modded-Selector-Comparison-20260907/`

The FCStd is a viewing derivative, not source authority. R7 is frozen; stock R1 is blue, Binky is orange, EREC is purple, and invalid source bodies are red.
