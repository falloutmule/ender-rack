# EnderRack license and redistribution notes

This file preserves provenance and license facts; it is not legal advice. No project-wide EnderRack license has been selected.

## Creality Ender-3

The pinned `Creality3DPrinting/Ender-3` repository contains a root GNU GPL version 3 license file. GitHub repository metadata also identifies the repository as GPL-3.0. The exact pinned root license is copied as `THIRD_PARTY_LICENSES/Creality_Ender-3_GPL-3.0.txt`.

The R2 and R5 coupons use dimensions and interface geometry derived from the official E plate. The repository-level GPL record is preserved, but this document does not independently determine the legal treatment of each hardware-CAD feature.

## Annex Engineering TradRack

At commit `f89dc0b115adfc49195d782c5d7ecd348a574891`, the top-level `LICENSE.md` states that the work is licensed under CC BY-NC-SA 4.0 and that a subfolder license takes precedence where present. The `CAD/` folder has no separate license file at that commit, so the pinned top-level notice is the applicable repository notice for the source CAD used here. The exact notice is copied as `THIRD_PARTY_LICENSES/TradRack_CC-BY-NC-SA-4.0_NOTICE.md`.

R5 uses the stock TradRack selector/MGN mounting pattern and selector envelope. Its artifact entry in `SOURCES.md` therefore records TradRack as an upstream dependency rather than treating R5 as provenance-free original geometry.

## Publication gate

Before a public release or production artifact is published:

1. Recheck the licenses at the pinned source revisions and any newly used upstream subfolders.
2. Preserve required attribution, notices, change identification, non-commercial terms, and share-alike obligations where applicable.
3. Review whether a combined artifact is derivative of one or both upstream CAD sources.
4. Select an EnderRack-wide license only after resolving compatibility and scope.
5. Do not imply upstream endorsement.

