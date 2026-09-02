# EnderRack Carriage Interface Invalidation Notice

**PHYSICAL FIT-CHECK FAIL — COMMUNITY CARRIAGE INTERFACE REJECTED**

Do not fabricate or continue production adapter, tensioner, belt-clamp, or endstop work from the carriage interface contained in:

- `../EnderRack_15Lane_Design.FCStd`
- `../EnderRack_Interface_FitCheck.FCStd`
- `../exports/EnderRack_Interface_FitCheck.step`
- `../exports/EnderRack_Interface_FitCheck.stl`

These files are preserved as forensic evidence and as a source for the unaffected TradRack and parametric lane work. They must not be treated as a verified Ender-3 V2 carriage interface.

The digital audit proved that the E1–E5 centers passed through the adapter, FCStd, STEP, and STL without a meaningful transform/export error. It also found that the selected community-CAD cylinders were not all equivalent mounting holes, although the coupon converted every center to a Ø3.40 mm clearance hole. The user’s physical fit-check established that the resulting pattern does not match the plate on this machine.

Resume interface design only after a measured carriage reference passes the paper template and primary PLA plate coupon defined in `PHYSICAL_MEASUREMENT_WORKSHEET.md`.

