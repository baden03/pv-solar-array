# Installation flow

End-to-end order of work from a bare container roof through an energized PV and battery plant. Use this as the **master sequence**; detailed specs and alternatives live in the linked documents.

**Safety:** Follow local electrical code, the hybrid inverter manual, and battery/BMS documentation. Keep PV and battery conductors de-energized when making connections until the step explicitly calls for energization. Use appropriate PPE and lockout/tagout where required.

---

## 1. Clean and inspect the roof

*   Remove debris, rust scale, and contaminants that would reduce magnet grip or damage roof paint.
*   Inspect corrugations, seams, and any existing penetrations; note high-stiffness lines for anchor and strap placement.
*   **Related:** [Mounting, ballast & thermal overview](./mounting_and_ballast.md) (array layout and phased anchoring).

---

## 2. Assemble the frame with solar panels

*   Build the mounting frame per manufacturer instructions and install modules with correct torque, clips, and grounding hardware as specified for the rail system.
*   Prefer completing heavy assembly at ground level if lifting equipment is limited; otherwise stage components on the roof without blocking access paths.
*   **Related:** [Mounting, ballast & thermal overview](./mounting_and_ballast.md) (Avoltik / tilt configuration), [Solar panel array](./solar_panel_array.md) (module choice and electrical layout).

---

## 3. Anchor the PV array with magnets

*   Place the eight magnet pads per the phased plan (4× stronger + 4× lighter duty), interfaces to roof skin verified on a coupon if needed.
*   Lash the frame to the pads; adjust pretension evenly and protect edges on straps or cables.
*   Confirm restraint against wind uplift and slide before proceeding to energized work on the roof.
*   **Related:** [Mounting, ballast & thermal overview](./mounting_and_ballast.md), [Solar ballast & thermal concepts](./solar_balast.md) — Phase 1 magnets; Phase 2/3 if adding water ballast or thermosiphon later.

---

## 4. Wire the solar panels

*   Complete string or parallel wiring per the module datasheet and inverter MPPT limits (voltage/current, polarity, and labeling).
*   Dress cables for drip loops, abrasion clearance over corrugations, and future service access.
*   Leave PV homerun ends at the inverter location **disconnected** until after the PV-side disconnect device is installed (next step).
*   **Related:** [Solar panel array](./solar_panel_array.md), [All-in-one inverter system](./inverter_system.md) (PV input ratings).

---

## 5. PV shutoff breaker (disconnect)

*   Install a **listed DC disconnect / PV breaker** (or equivalent PV rapid-shutdown-compliant assembly, per jurisdiction) between the array wiring and the hybrid inverter PV input so the array can be isolated for service.
*   Label circuits clearly (polarity, string ID, hazard warnings).
*   **Related:** [All-in-one inverter system](./inverter_system.md).

---

## 6. All-in-one solar charger / inverter

*   Mount the hybrid MPPT inverter-charger securely; provide ventilation per the manual.
*   Route PV input, battery DC, and AC cabling (including grid/generator if used) through appropriate strain relief, glands, or conduit per code.
*   **Do not enable PV or battery currents** until terminations are torqued, polarities verified, and the next-step protection devices are coordinated with the installer manual’s commissioning sequence.
*   **Related:** [All-in-one inverter system](./inverter_system.md).

---

## 7. Breakers / overcurrent protection

*   Fit **DC-side** protection and disconnect as required between the battery bank and the inverter (manual, BMS, and code may specify breaker class, fuse rating, and location).
*   Add **AC-side** overcurrent and RCD/protection devices on inverter output (and input if grid-tied) per product documentation and local rules.
*   Coordinate ratings with the bank’s main fuse or breaker (see battery document).
*   **Related:** [LiFePO₄ battery bank](./battery_bank.md) (e.g. main fuse and shunt layout), [All-in-one inverter system](./inverter_system.md).

---

## 8. Battery bank

*   Complete the pack, BMS, shunt, and enclosure per the bank design; verify cell matching, torques, and BMS communication before closing the DC path to the inverter.
*   With the inverter’s battery breaker **open**, make final battery terminals; then commission per inverter instructions (typical workflows close the battery disconnect before or after PV — **follow the manual** exactly).
*   **Related:** [LiFePO₄ battery bank](./battery_bank.md).

---

## Commissioning checklist (summary)

Before declaring the system live:

| Check | Done |
|--------|------|
| Magnet / mechanical anchor inspection | ☐ |
| PV disconnect opens under load test (when safe) | ☐ |
| Polarities verified at inverter and battery | ☐ |
| BMS alarms and inverter faults cleared | ☐ |
| Loads staged; no unchecked shorts | ☐ |

---

## Related documentation

| Document | Role |
|---------|------|
| [Mounting, ballast & thermal](./mounting_and_ballast.md) | Roof layout, phased anchors, orientation fallback |
| [Solar ballast & thermal](./solar_balast.md) | Magnets detail (Phase 1), water ballast (Phase 2), thermosiphon (Phase 3) |
| [Solar panel array](./solar_panel_array.md) | Modules and array electrical design |
| [All-in-one inverter system](./inverter_system.md) | Hybrid inverter/charger specs and manual |
| [LiFePO₄ battery bank](./battery_bank.md) | Cells, BMS, fusing, assembly |
| [Floating garden & biofilter](./floating_garden_biofilter.md) | Optional water/thermal periphery — not required for baseline electrical commissioning |
