# EnderRack source and artifact provenance

Complete upstream CAD archives and assemblies are intentionally not committed. Paths below identify the local packaging machine; upstream URL, commit/blob, filename, byte size, and SHA-256 make the sources reproducible.

## Upstream sources

| Source | Identity | Local file | Bytes | SHA-256 | Role |
|---|---|---|---:|---|---|
| Creality Ender-3 official mechanical CAD | Repository `https://github.com/Creality3DPrinting/Ender-3`; commit `88c7758cea9d0d00a54fdb238bedb3b33425f409`; path `Ender-3 Mechanical/STP/Ender3.STEP`; blob `30c9b930c0cc094b4d02acd72d71d835d7225c72` | `work/sources/ender-rack/official-ender3/Ender3.STEP` | 29,867,304 | `7E868F30A44F0E6B1DD0DAF8AF1D7810AD9A754CC6FA066F6EF4D2B81E3297AF` | Correct donor assembly and E-plate reference |
| Creality Ender-3 Fusion source | Same repository/commit; path `Ender-3 Mechanical/F360/Ender 3.f3d`; blob `998bd68bf940c3bd691fa9d7ead705bfa401e323` | `work/sources/ender-rack/official-ender3/Ender 3.f3d` | 6,344,736 | `95909A53CCFAC0E4F3EFEC9B964780D5602B453F441274DFEBB4B5D18C2BC726` | Provenance reference; not imported for controlling geometry |
| TradRack R1 STEP archive | Repository `https://github.com/Annex-Engineering/TradRack`; commit `f89dc0b115adfc49195d782c5d7ecd348a574891`; path `CAD/Trad_Rack_R1_2024-03-04_STEP.7z`; blob `c1dbef9f292f7f7a3bec446b092be2f23ef4702f` | `work/sources/ender-rack/Trad_Rack_R1_2024-03-04_STEP.7z` | 91,473,657 | `BE7646216D6483DA49B548B7225BF3A64F07A12960D89EE659F0D2CCB5F271E8` | Stock selector and lane reference |
| TradRack extracted default STEP | Extracted from the pinned R1 archive | `work/sources/ender-rack/TradRack_STEP_extracted/trad_rack_(default).STEP` | 116,600,287 | `19459C5098A6C084D50F77AB4FBDBFABAB48D6845C84B3E9159F50776083BDB3` | Imported reference assembly |
| Community Ender-3 V2 STEP | Community source recorded in historical audit | `work/sources/ender-rack/Creality-Ender3-V2-rev4.STEP` | 36,580,869 | `D81BDE4587B3237FDA23515AD524482A8F0D153226B952A3B3734CBC29D3B5D0` | **Rejected wrong-machine reference; provenance only** |

## Tracked artifact dependencies

| Tracked artifact | Upstream dependency | Classification | Validation scope |
|---|---|---|---|
| `cad/fit-checks/Ender3_Official_Carriage_FitCheck_R2.FCStd` and matching exports | Official Creality E-plate hole pattern, seating face, orientation, and boss relationship | Reference-derived project fit coupon | Physical PASS only for exercised carriage-interface features |
| `cad/working/EnderRack_Selector_Interface_Coupon_R5.FCStd` and matching exports | R2-validated Creality interface plus TradRack selector/MGN mounting pattern and selector envelope | Substantially project-designed, upstream-interface-derived coupon | Digital PASS; real-selector physical test pending |
| Technical renders and verification records | Corresponding R2/R5 artifacts | Evidence | Do not treat images as dimensional authority |

Reference FCStd files that embed complete upstream assemblies remain local-only and are listed in [HASHES.md](HASHES.md).

