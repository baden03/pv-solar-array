# Mounting, Ballast & Thermal Management

The goal is to secure solar panels on a shipping container **without drilling the roof**. The roadmap is phased: start with removable magnetic anchors and lashing, add or transition to simple water ballast for mass and stability, then expand into passive thermosiphon thermal integration when the hydraulic path is warranted.

---

## Array layout (common to all phases)

*   **Mounting system**: **[Avoltik Solarpanel Halterung für 4 Module (10°)](https://pv-insel.de/products/avoltik-solarpanel-halterung-fur-4-module-komplettset-fur-solarmodule-bis-2000-1200-mm)**.
*   **Configuration**: Central North–South ridge; two panels at 10° east, two at 10° west.
*   **Airflow**: The mounting hardware maintains an air gap (≥10 cm) between panel backsheets and the container roof for passive convective cooling.
*   **Maintenance**: The 10° tilt is modest for self-cleaning; panels may need more frequent manual rinsing than steeper installs.

Anchoring detail, water ballast layouts, and thermosiphon concepts are documented in **[Solar Ballast System & Thermal Integration Concepts](./solar_balast.md)**.

---

## Phased roadmap

### Phase 1 — Magnetic anchors (no penetration)

*   Use **four 250 kg-rated** magnets and **four 150 kg-rated** magnets as discrete roof anchor pads.
*   **Lashing** ties the PV mounting frame to these pads so the assembly resists uplift and shear without fasteners through the roof skin.
*   Magnets suit steel container roofs when the alloy and finish allow reliable grip; shear and peeling limits, pad footprint, slip coefficients, and weather exposure must be validated for your unit (see linked doc for placeholders).

Phase 1 is the minimum viable anchor path before adding ballast mass.

### Phase 2 — Simple water ballast

*   **Add** water ballast to increase stabilizing mass, reduce reliance on friction at magnet pads during gusts, and spread load — or **replace** magnets if ballast alone meets structural targets and maintenance preference.
*   Phase 2 is intentionally “dumb”: static water in pipes/tanks only, **no thermosiphon** requirement.

### Phase 3 — Thermosiphon and thermal coupling

*   Expand the Phase 2 water network into elevated storage, rainwater integration, booster loops, optional garden-coil cooling, and passive circulation for panel-adjacent cooling and domestic pre-heat — as described in the ballast document.

---

## Contingency (orientation)

If the east/west pair does not meet performance targets, the same mounting hardware can be reconfigured into **two separate south-facing banks** at about **23°** tilt for higher peak irradiance alignment.

---

## Design history

Earlier drafts treated water ballast as the primary anchor from day one and described a thermosiphon “future plan” separately. The current documents separate **anchors (Phase 1)** from **mass (Phase 2)** from **active thermal coupling (Phase 3)** so magnet-only deployment is explicit. For evolving ballast geometry, BOM, and thermal subsystems, see **[Solar Ballast System & Thermal Integration Concepts](./solar_balast.md)**.
