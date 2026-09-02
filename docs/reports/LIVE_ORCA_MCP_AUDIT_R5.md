# EnderRack R5 live Orca MCP slice audit

## Classification

- `LIVE_ORCA_MCP_PASS = PASS`
- `CURRENT_ENDERRACK_TEST_ARTICLE_SLICED = PASS`
- `READY_FOR_PHYSICAL_COUPON_PRINT = NO`

R5 is the only model on the live plate. R4 was explicitly removed before orientation and slicing.

## Source and placement

| Field | Value |
|---|---|
| STL | `C:\Users\fallo\Documents\Codex\2026-08-30\set-up-freecad-mcp-on-this\outputs\ender-rack\exports\EnderRack_Selector_Interface_Coupon_R5.stl` |
| STL SHA-256 | `6070C29687531215B4A7D58FBD1C77B53CB3CB9BBB349A0F10DA72946EF2EBAC` |
| Scale | 100% |
| Rotation | `(90, 0, 0)` degrees |
| World size | 61.500 × 40.550 × 22.250 mm |
| Placement | PASS; broad steel-contact face on bed; overflow 0 mm |

## Profiles and settings

- Printer: `Creality Ender-3 V2 0.4 nozzle`
- Filament: `Creality Generic PLA`
- Process: `0.20mm Standard @Creality Ender3V2`
- 0.20 mm layers; 3 walls; 4 top / 3 bottom layers; 15% crosshatch.
- Generated supports disabled. The retained triangular gussets provide modeled support for the selector-block overhang.
- Auto brim configured; skirt 0.

## Slice result

| Field | Result |
|---|---:|
| State | done, valid, 100% |
| Layers | 111 |
| Time | 1 h 29 m 59 s |
| Filament | 4,300.605 mm / 12.827 g |
| G-code bytes | 2,231,066 |
| G-code SHA-256 | `89EDF29DC7298A7ACCB3A3A6581DD54F20C12D2DCECBDBDB27B11E5AC0F54541` |

G-code: `C:\Users\fallo\Documents\Codex\2026-08-30\set-up-freecad-mcp-on-this\outputs\ender-rack\slice-results\live-orca-mcp-r5\EnderRack_Selector_Interface_Coupon_R5.gcode`.

Renders:

- [Oriented editor view](renders/post-orient-iso/render_plate-0.png)
- [Sliced isometric](renders/sliced-preview-iso/render_plate-0.png)
- [Sliced top](renders/sliced-preview-top/render_plate-0.png)
- [Sliced front/gussets](renders/sliced-preview-front/render_plate-0.png)

## Warning gate

Orca still reports level-3 warning `1000C001` / `bed_temperature_too_high_than_filament` because the native profile sets the bed and PLA vitrification values both to 60 °C. No material temperature was guessed or changed. Therefore this G-code is diagnostic evidence only and `READY_FOR_PHYSICAL_COUPON_PRINT` remains NO until an approved/spool-specific bed temperature is supplied and the part is freshly sliced.
