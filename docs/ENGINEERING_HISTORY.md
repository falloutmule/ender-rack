# EnderRack engineering history

This document records engineering events that occurred before this directory entered Git. They are not represented as retrospective Git commits.

## 1. Ender-3 V2 source rejected

A community `Creality-Ender3-V2-rev4.STEP` assembly was imported and used for early feasibility and interface work. A physical coupon did not match the donor carriage. Subsequent machine identification established that the donor was not mechanically a V2. V2-derived fabricated-fit work was rejected and archived.

## 2. Official original Ender-3 source adopted

Official Creality Ender-3 CAD at commit `88c7758cea9d0d00a54fdb238bedb3b33425f409` was imported through FreeCAD MCP. The import contained 1,243 objects and passed null-geometry, topology, placement, save/reopen, and recompute checks. The official X gantry and `E plate` were isolated.

## 3. Official E-plate R2 physical carriage fit PASS

The first official-CAD coupon correlated the hole pattern but could not seat over two retained hotend bosses. R2 added clearance pockets and physically fit the real plate. The official E plate was promoted only for the interface features exercised by R2.

## 4. Secondary selector-interface digital PASS

The carriage-to-selector interface was rebuilt from the validated reference. Revisions corrected an overhang/load path and a weak wheel-edge ligament. R5 provides 5 mm lateral and lower wheel-relief ligaments, two full-height triangular gussets, and four blind temporary selector pilots.

## 5. Current gate pending

R5 is digitally valid but has not passed the real-selector physical test. The available G-code is diagnostic only because it used a V2 printer preset and carries an Orca material-temperature warning. Correct profile selection and re-slicing precede the physical test.

