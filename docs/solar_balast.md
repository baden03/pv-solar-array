# Solar Ballast System & Thermal Integration Concepts

This document describes a **three-phase** approach to anchoring PV on a shipping container roof without drilling: **magnetic anchor pads and lashing (Phase 1)**, **simple static water ballast (Phase 2)**, and **thermosiphon-based thermal integration (Phase 3)**. It keeps modular, low-cost expansion in mind and preserves prior water-only concepts as Phase 2/3 content.

---

## Overview

| Phase | Role | Penetration |
|-------|------|-------------|
| **1** | Magnetic pads + lashing secure the frame to the roof | None |
| **2** | Water mass adds or replaces magnetic reliance for overturning and sliding | None (vessels on roof) |
| **3** | Same water path used for passive circulation, cooling, and hot-water pre-heat | None through roof; hose-level connections only |

Phases can overlap in time (e.g. Phase 1 + partial Phase 2) but the **design intent** is sequenced: prove anchor/lash, then add ballast, then plumb for thermosiphon.

---

## Phase 1 — Magnetic anchor pads and lashing

**Purpose:** Create **eight** rated anchor points on a ferromagnetic container roof so the Avoltik (or equivalent) frame can be **lashed down** without drilling.

**Target inventory (conceptual):**

*   **4×** magnets rated for **~250 kg** normal pull (manufacturer definition and test conditions matter — see below).
*   **4×** magnets rated for **~150 kg** normal pull.

**Layout intent:**

*   Pads are placed to align with the mounting frame’s reaction points (corners, rail nodes, or paired lugs), not necessarily in a single grid — final positions follow statics of the frame and container stiffeners.
*   **Lashing** (webbing, turnbuckles, chain with appropriate edge protection, or equivalent) transfers tension/compression from the frame into the magnets while limiting peel on the magnet face.

**Engineering notes (to be expanded):**

*   Catalog pull ratings are usually **normal to a clean steel plate**; real roofs have paint, ripples, and alloy variation — **de-rate** and test on your door/skin sample.
*   Wind uplift on tilted panels can produce **peel and sliding**; magnetic friction is finite — Phase 2 ballast often helps even when magnets remain in service.
*   Weather: pad covers, drainage, and corrosion on magnet hardware should be specified so the system does not degrade invisibility between inspections.

A future revision of this document can add pad geometry, soft-interface materials, lashing patterns, and a simple load sketch. **Phase 1 detail is intentionally brief here** until those items are fixed for your container and wind zone.

---

## Phase 2 — Simple water ballast (static mass)

**Purpose:** Add **weight** and a distributed footprint with **no requirement** for thermal loops or thermosiphon. Water can **supplement** magnet anchors or, if analysis allows, **replace** them after ballast volume is proven.

### Recommended layout: 110 mm PVC-U zig-zag

**Current reference build:**

*   6 × 110 mm diameter PVC pipes, 4 m long (main runs)
*   5 × 0.5 m cross-over runs
*   10 × 90° elbows for zig-zag routing
*   Total pipe length: 26.5 m
*   Total ballast: ~252 L ≈ **~252 kg of water**
*   Estimated material cost: **~€290**
*   Wall thickness: 2.7 mm PVC-U (suitable for non-pressurized static water)

**Advantages:**

*   Fewer joints from 4 m lengths → fewer leak points
*   Zig-zag improves structural stiffness of the wet frame
*   Geometry is **compatible** with later Phase 3 routing (cold low / warm high) if sloped intentionally during install

**Phase 2 flow control (optional, not thermosiphon):**

*   Fill/drain hose bibs only; **no reliance** on natural circulation yet.
*   If Phase 3 is likely, installers can preset a slight continuous rise toward the intended high outlet to avoid rework.

**Installation:**

*   Mount on roof supports independent of magnets or integrated with lash points per your final BOM.
*   UV-stabilized PVC-U under panel shade lasts well; straps should not concentrate load on corrugated valleys without spreader pads.

### Pipe sizing considerations

**Smaller diameter (e.g. 110 mm):**

*   Lower cost, easier handling, common fittings
*   Modularity and layout flexibility
*   Faster thermal response **if/when** Phase 3 activates
*   More joints than fewer large ducts; more leakage vigilance

**Expansion:**

*   Add parallel runs or bridge to larger (e.g. 200 mm) vessels later.

### Alternate concept: original 200 mm U-shape (reference)

*   2 × 200 mm diameter PVC pipes, 4 m long, elbowed into a **U**, with midpoint T-bracing and top/bottom hose ports.
*   Approximate volume **~280 L (~280 kg)**.
*   Still valid as a coarse Phase 2 block of mass where fewer pieces are preferred.

### Phase 2 next steps

*   Assemble the chosen pipe grid; add drain/fill with valves.
*   Confirm combined **magnet + water** overturning/sliding margins for your exposure, or document magnet removal if retiring Phase 1.

---

## Phase 3 — Thermosiphon & thermal integration

**Purpose:** Turn the Phase 2 water inventory into **thermal mass** coupled to PV cooling and optionally domestic pre-heat, using passive density-driven flow where practical.

### Core concept: combined thermosiphon + rainwater cooling

*   Ballast volumes gain heat from ambient and panel vicinity.
*   Hotter water rises along an ascending path toward an elevated **thermal buffer** (e.g. insulated rain barrel).
*   At high tank level or temperature, cooler makeup (rainwater, diverter-fed) can **submerge** warmer ballast water and restore a heat-sink role under the array.

**Thermal buffer barrel (conceptual):**

*   Elevated versus ballast inlet/outlet to support thermosiphon head.
*   Hot water reservoir for use; cold feed available to **refresh** ballast when cooling PV is the priority.

Routing aligned with Phase 2 zig-zag:

*   Cold entry at low end of zig-zag; hot exit high, toward barrel inlet — **planned slope** matters.

---

## Two-stage thermosiphon (Phase 3 enhancement)

**Concept:**

*   Primary ballast remains mostly shaded under panels (mass + panel-adjacent cooling).
*   A **secondary sun-exposed** pipe run along the uphill path **preheats** return water before it enters the barrel, increasing ΔT and circulation vigor.

**Benefits:**

*   Stronger thermosiphon, faster turnover, higher top temperatures for use
*   Modular add-on along roof edge, wall, or guardrail
*   Optional **radiator-like** nighttime cooling behavior

**Notes:**

*   Match 110 mm mains or slim booster line (50–75 mm) trade velocity vs ΔT gain.
*   Black booster surface; continuous rise to barrel inlet; allowance for thermal expansion.

---

## Floating garden & garden coil (Phase 3, optional)

**Roles:**

| Function | Description |
|---------|-------------|
| **Rainwater / biology** | Open-top garden tank receives pre-filtered water; raft plants aid clarity |
| **Cool-side bleed** | Submerged coil knocks temperature off the return leg before ballast inlet |
| **ΔT booster** | Cooler ballast inlet strengthens thermosiphon driving head |

Hot-barrel discharge can route through this coil (~50–100 L tank minimum; 32–50 mm submerged coil common in concept studies). Overflow strategy remains separate from structural ballast sizing.

---

## Performance expectations (Phase 3, indicative)

Rough summer ranges for a well-instrumented passive loop:

| Component | Estimated range | Notes |
|-----------|-----------------|--------|
| Sun-exposed booster | 45–65 °C | Black pipe |
| Ballast under PV | 35–45 °C | Shaded plus panel spill |
| To hot barrel | 40–60 °C | Flow-dependent |
| Insulated barrel top | 50–65 °C | Stratified |
| Garden coil zone | 20–30 °C | Shaded / evaporative |
| Ballast inlet after coil | 25–35 °C | Improves circulation ΔT |

Cooler/overcast approximations: booster 30–45 °C, ballast ~25–35 °C, barrel top ~35–45 °C, coil-linked points lower by ~10–15 °C band.

Use logged probes at booster, ballast inlet/outlet, barrel top/bottom, and coil exit — ESP-class loggers suffice.

---

## Master next steps (all phases)

1. **Phase 1:** Freeze magnet model, pad interface, eight-point lashing plan, and inspection checklist on your roof sample.
2. **Phase 2:** Build wet mass; prove leak regimen and strap loads; reconcile with magnets (retain vs remove).
3. **Phase 3:** Elevate buffer tank, establish continuous rise paths, connect booster optionally, then iterate on temperatures and summertime panel back-surface metrics.
