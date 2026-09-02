# EnderRack selector-interface coupon R5

## Status

**DIGITAL PASS — PHYSICAL REAL-SELECTOR TEST REQUIRED**

Fabrication status: **PROVISIONAL — FIT-CHECK FABRICATION ONLY. DO NOT FABRICATE PRODUCTION PARTS.**

R5 supersedes R4. The user-identified failure location was the lateral ligament between the `X=0` wheel-clearance hole and the outside edge. R4 strengthened the lower ligament but accidentally left only approximately 0.25 mm laterally at this exact location.

## Correction

- Wheel-clearance radius: 5.75 mm.
- Minimum material from each wheel relief to its outside X edge: **5.00 mm**.
- Minimum material below each wheel relief: **5.00 mm**.
- R5 X extent: `-10.75 .. +50.75 mm`; the two wheel centers remain `X=0` and `X=40 mm`.
- The two full-height triangular selector-block gussets are retained. They support the cantilevered selector block and address a different load path from the wheel-edge ligament.
- The four selector-block holes remain intentionally blind Ø2.7 × 6.5 mm temporary M3 pilots.

## Verification

| Check | Result |
|---|---:|
| Bounding box | 61.500 × 22.250 × 40.550 mm |
| Volume | 23,459.308 mm³ |
| Topology | One valid solid |
| Circled lateral ligament | 5.000 mm, formerly 0.250 mm |
| Opposite wheel lateral ligament | 5.000 mm |
| Lower wheel ligament | 5.000 mm |
| Selector/coupon intersection | 0.000 mm³ |
| Coupon/wheel-envelope intersection | 0.000 mm³ |
| Coupon/conservative-belt intersection | 0.000 mm³ |
| R2 contact-layer missing volume | 0.000 mm³ |
| STEP BRep distance | 0.000 mm |
| STL bbox maximum delta | 7.63e-7 mm |
| STL facets | 1,520 |

Machine-readable verification: `../../work/ender-rack-inventory/ender_rack_selector_interface_coupon_r5_verification.json`.

## Artifacts

| Artifact | Bytes | SHA-256 |
|---|---:|---|
| `EnderRack_Selector_Interface_Coupon_R5.FCStd` | 17,536,897 | `B1EFD105F3B6D260C9538530F6B6DCBD37D0BAF2DC2C60AE2D66472AFE44FA49` |
| `exports/EnderRack_Selector_Interface_Coupon_R5.step` | 79,900 | `A471DE9772790A6DEC882545069C8CBD4F0CE840D9EA4DB57C37403A67E531C4` |
| `exports/EnderRack_Selector_Interface_Coupon_R5.stl` | 76,084 | `6070C29687531215B4A7D58FBD1C77B53CB3CB9BBB349A0F10DA72946EF2EBAC` |

Evidence renders:

- [Coupon-only isometric](screenshots/EnderRack_Selector_Interface_Coupon_R5_CouponOnly_Isometric.png)
- [Selector-facing](screenshots/EnderRack_Selector_Interface_Coupon_R5_CouponOnly_SelectorFacing.png)
- [Steel-contact](screenshots/EnderRack_Selector_Interface_Coupon_R5_CouponOnly_SteelContact.png)
- [Gusset plan](screenshots/EnderRack_Selector_Interface_Coupon_R5_CouponOnly_GussetPlan.png)

R5 is the current printable CAD source. R4 and earlier revisions are preserved but must not be used for the next fit check.
