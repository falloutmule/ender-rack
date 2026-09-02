# EnderRack durable decisions

These are design decisions, not a conversation transcript.

1. The donor is mechanically an original/older Ender-3-family machine, not an Ender-3 V2. Display appearance does not establish mechanical identity.
2. The community `Creality-Ender3-V2-rev4.STEP` is rejected for fabricated-fit work. V2 interface coordinates, transforms, and collision results are superseded.
3. Official Creality Ender-3 CAD is the selected donor reference. The official `E plate` is controlling only for carriage-interface features physically exercised by the R2 coupon.
4. R2 physically validated the fastener pattern, orientation, steel seating face, and boss-clearance relationship. It did not validate every E-plate contour, belt datum, or wheel-stack depth.
5. The R2 boss pockets are clearance features, not precision locators. Their generated geometry is approximately diameter 5.5 mm by 5.2 mm deep; the earlier 5 x 5 mm values are successful nominal inputs, not measured boss dimensions.
6. The primary lane target is 15 at 17 mm pitch, with a 238 mm first-to-last span. The fallback is 12 lanes at 187 mm.
7. Sixteen lanes is intentionally not pursued without an explicit reopening. Seventeen lanes is excluded by the approximately 270 mm physical travel observation.
8. The Ender V-wheel stage is intended to replace the TradRack MGN9 selector stage while retaining the mostly stock selector architecture.
9. R5 supersedes R4 and all V-notch instructions. The motor-side cross remains; the tensioner side is identified by the opposite reinforced wheel-edge.
10. The current static transform is `(+15.000, +22.250, -20.300) mm`, with zero roll/pitch/yaw. Earlier transforms are not controlling.
11. A validated static coupon must precede a full motion model. CAD capability alone does not authorize downstream geometry.
12. End-of-travel collision work must use the validated interface and physical tensioner evidence. Extra stand-off must not be used to solve an unverified dynamic problem.
13. Production material is not established by the PLA fit-check. PLA is for fit testing; a production part requires a later material and load decision.
14. Happy Hare/Klipper remains the intended control strategy. The donor electronics board revision must be read from the physical board before pin planning.

