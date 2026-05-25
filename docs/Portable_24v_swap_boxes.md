# Portable / Hot-Swappable 24 V LiFePO₄ Battery Packs (~100 Ah)

## Overview

This document describes **modular ~100 Ah, 24 V LiFePO₄ packs** meant to be hot-swapped, carried, and redeployed (base, vehicle, boat, expedition). It covers design goals, internal architecture, connectors, parallel use, charging philosophy, balancing concepts, safety, and operating modes.

**How swap-boxes charge from the container’s solar** (dedicated auxiliary PV array, auxiliary MPPT, **battery-side** destination routing, dual-array independence) is specified in the companion:

**→ [Supplement — Dual Independent PV Arrays and Battery-Side Auxiliary MPPT Routing](./pv_routing_swapbox_supplement.md)**

That supplement uses **`Aux PV → Auxiliary MPPT → BAB or Swap-Box`** (selector after the auxiliary MPPT) and **`Main PV → AIO MPPT → BAB`** with **no** PV string transfer or MPPT sharing. Direct **battery-to-battery** charging from BAB into a swap-pack is **not** the plan—charge enters packs via **MPPT** or approved chargers. This file stays **pack-level**; array layout, auxiliary MPPT coordination, switching sequences, and dual-charger etiquette on BAB live in the supplement.

Target characteristics for the pack ecosystem:

- modular  
- serviceable (where the enclosure allows)  
- marine-capable  
- off-grid-capable  
- hot-swappable  
- transportable  
- long-storage-friendly  
- emergency-deployable  

---

## 1. System philosophy

The packs are intended to serve multiple operational modes:

| Mode | Purpose |
|------|---------|
| Daily use | Site-supported use: one pack on loads while another charges from the **dedicated auxiliary array → auxiliary MPPT** when that output is routed to the swap-pack (see supplement), or via shore / vehicle / other approved charger |
| Weekend mode | Single-pack portable power away from base |
| Travel mode | 1–3 week excursions |
| Expedition mode | Multi-month off-grid with rotation / redundancy |
| Winterization mode | Long-term storage of all packs |
| Emergency / Bug-out mode | Rapid evacuation / marine deployment |

Modules stay **energy units** you move between contexts—not a single permanent install.

Independence from any one tether:

- not locked to one building or vessel layout  
- at the container, the swap-pack is fed by **its own auxiliary PV chain** and **battery-side routing**—not direct DC from BAB nor shared MPPT PV inputs (see [supplement](./pv_routing_swapbox_supplement.md))  

---

## 2. Pack architecture and charging context

### Swappable 100 Ah modules (design focus)

- 24 V nominal LiFePO₄  
- ~100 Ah per pack (~2.5 kWh)  

**Typical field set:**

- 2 × packs  
- removable and chargeable independently  
- parallel-capable subject to §9  

**Candidate hardware (under consideration):** [AliExpress — item 1005009726658632 24v 100ah](https://de.aliexpress.com/item/1005009726658632.html).

### Charging at base — dedicated auxiliary PV and MPPT output routing

When moored at the container install, the swap-pack charge path uses a **physically separate auxiliary PV array** (not shared or switched with main array strings):

```text
Auxiliary PV array → Auxiliary MPPT → (battery-side A/OFF/B) → Portable swap-box
```

Concurrently on the stationary side:

```text
Main PV array → All-in-One MPPT → BAB
```

The auxiliary MPPT output may alternatively be routed to **BAB** instead of the swap-pack; **two MPPT chargers feeding one battery** under aligned setpoints is normal—see **[Supplement — Dual Independent PV Arrays and Battery-Side Auxiliary MPPT Routing](./pv_routing_swapbox_supplement.md)**.

**Important:** Avoid ad-hoc **BAB ↔ swap-pack DC jumpers** for charging; use the **regulated auxiliary MPPT** path (destination selected on the battery side), or discrete AC/DC chargers as appropriate.

### Other charging sources

When away from base or as a supplement:

- shore **AC → DC** LiFePO₄-aware charger  
- vehicle or boat DC (only where voltage, current, and BMS rules allow)  
- portable PV with its **own** MPPT—not by tapping the container’s auxiliary or main PV homeruns without a full redesign  
---

## 3. Design goals

### Required features — electrical

- 24 V native  
- LiFePO₄ chemistry  
- integrated BMS  
- fused outputs  
- high-current capable  
- inverter capable (when used with an appropriate external inverter)  
- DC direct loads preferred  

### Required features — mechanical

- waterproof or splash resistant  
- impact resistant  
- marine-safe  
- easy carry handles  
- stackable  
- serviceable  
- modular  

### Required features — operational

- hot-swappable  
- independently chargeable  
- field deployable  
- rapid disconnect  
- long-storage capable  

---

## 4. Why 24 V?

24 V was selected because:

| Advantage | Benefit |
|-------------|---------|
| Lower current | Smaller cables |
| Higher efficiency | Less voltage drop |
| Better inverter performance | Lower stress |
| Easier scaling | Boat / vehicle integration |
| Industrial ecosystem | Better hardware availability |

---

## 5. Why LiFePO₄?

| Feature | Benefit |
|---------|---------|
| Long cycle life | Thousands of cycles |
| Thermal stability | Safer than NMC |
| Flat voltage curve | Excellent inverter behavior |
| Deep cycling capability | Good off-grid use |
| High efficiency | Excellent solar storage |

---

## 6. Portable pack internal design

### Proposed configuration

- 8S LiFePO₄  
- 24 V nominal  
- ~100 Ah  

### Internal components

| Component | Purpose |
|-----------|---------|
| Cells | Energy storage |
| BMS | Protection + balancing |
| Main fuse | Catastrophic fault protection |
| Disconnect switch | Manual isolation |
| Anderson connector | High-current quick disconnect |
| DC breaker(s) | Load protection |
| USB-C PD modules | Device charging |
| Optional DC outputs | Direct 24 V appliances |

At the container, **photovoltaic energy** enters the electrical system only via **appropriate MPPT PV inputs**: for the portable pack chain, via the **fixed auxiliary PV array → auxiliary MPPT → pack** path (never raw strings to pack studs)—see [supplement](./pv_routing_swapbox_supplement.md).

---

## 7. Connector standardization

### Anderson connectors

Preferred ecosystem standard for **pack DC** (loads, parallel mates, chargers that connect at the battery DC bus). The **fixed auxiliary PV home runs** terminate at PV isolators and the auxiliary MPPT per the [supplement](./pv_routing_swapbox_supplement.md).

#### Advantages

| Advantage | Reason |
|-----------|--------|
| Genderless | Simple field use |
| High current | Suitable for inverter loads |
| Reliable | Industrial proven |
| Hot-plug capable | Better for modularity |
| Easy replacement | Field repairable |

#### Recommended connector types

| Connector | Use |
|-----------|-----|
| Anderson SB50 | Main pack power |
| XT60 / XT90 | Small accessory systems |
| USB-C PD | Consumer electronics |

---

## 8. Hot-swap philosophy

The portable packs are intended to:

- connect/disconnect rapidly,  
- without major rewiring,  
- without opening enclosures (for normal swaps),  
- without tools (for connectorized paths).  

### Example use cases

**At base (container / workshop)**

- one pack on loads  
- second pack charging from **auxiliary MPPT** when selector targets swap-pack (**battery-side routing**—see [supplement](./pv_routing_swapbox_supplement.md)); future automation likewise stays on battery output, not PV strings  
- or charging from shore / AC charger when that path is disconnected or idle  

**Boat or vehicle**

- one pack in service  
- one spare charging  

**Emergency**

- remove packs rapidly  
- deploy to vehicle or vessel  

---

## 9. Parallel operation

Research and practice suggest:

- modern LiFePO₄ packs with proper BMS systems can be paralleled safely **provided**  
  - voltage delta is small at connect time.  

This addresses **pack-to-pack** paralleling for load sharing. It does **not** supersede **[supplement](./pv_routing_swapbox_supplement.md)** discipline: swap-pack charging flows through **regulated MPPT/aux paths**, not improvised BAB↔pack DC ties.

### Practical guidelines — safe parallel connection

| Condition | Recommendation |
|-----------|----------------|
| Voltage delta < 0.1 V | Generally safe |
| Similar chemistry | Required |
| Similar cell count | Required |
| Similar nominal voltage | Required |

---

## 10. Charging philosophy

### Normal use

Do **not** hold at 100 % SOC continuously when avoidable.

Instead:

- cycle on real loads or solar,  
- periodically reach top balance per BMS / service needs.  

**Two independent container arrays:** there is **no** PV-string transfer—the main and auxiliary trackers each serve **their own** array. Follow **[supplement](./pv_routing_swapbox_supplement.md)** for isolators, commissioning order, auxiliary output destination, and auxiliary↔BAB coexistence assumptions.

### Long-term storage

Target:

- ~50–60 % SOC  
- cool environment  
- disconnected loads  

### Recommissioning

Before returning to service:

1. Inspect  
2. Reconnect  
3. Charge slowly  
4. Top balance if necessary (see §11 for cell-level service; else follow manufacturer)  
5. Validate pack behavior  

---

## 11. Top balancing procedure (cell-level service)

Use this **only** if you intentionally open a pack and work at cell level (e.g. custom build or deep service). **Sealed commercial packs** should follow the manufacturer unless you accept voided warranty and added risk.

### Procedure summary

1. Disassemble pack into parallel cell configuration  
2. Equalize naturally in parallel  
3. Top charge parallel block using single-cell LiFePO₄ charger  
4. Allow absorption taper  
5. Rest overnight  
6. Verify convergence  
7. Rebuild into 8S pack  

---

## 12. Charging profiles

Targets for **24 V nominal** packs when configuring **battery-side** regulation (auxiliary MPPT targeting swap-pack, shore charger, or equivalent). **Auxiliary Voc/Isc sizing** sits at **that array ↔ auxiliary MPPT** interface—see [supplement](./pv_routing_swapbox_supplement.md) §§9–10.

### Operational profile

| Setting | Typical target |
|---------|----------------|
| Bulk / absorption | ~27.8 V |
| Float | ~27.0 V or disabled |
| Daily SOC | 20–90 % preferred |

### Storage profile

| Setting | Target |
|---------|--------|
| SOC | 50–60 % |
| Charging | Maintain storage SOC only |
| Loads | Disconnected |

### Expedition / Zombie profile

| Setting | Goal |
|---------|------|
| Maximum usable energy | Prioritize |
| Full charge allowed | Yes |
| Deep cycling allowed | Yes |
| Redundancy prioritized | Yes |

---

## 13. Operational modes (100 Ah packs)

### Mode 1 — Site-supported daily use

- Run selected loads from one pack  
- Charge a second pack at base via **auxiliary PV → auxiliary MPPT → swap-pack** routing (selector position per [supplement](./pv_routing_swapbox_supplement.md)), or via approved non-solar chargers when needed  

### Mode 2 — Weekend trip

**Single pack:**

- lighting  
- USB charging  
- Starlink  
- coolbox  

### Mode 3 — Expedition

**Two packs:**

- rotation charging  
- redundancy  
- mobile off-grid living  

### Mode 4 — Winterization

**All packs:**

- disconnected from loads/chargers unless maintaining storage SOC  
- reduced SOC (~50–60 %)  
- stored cool and dry  

### Mode 5 — Bug-out / Zombie mode

**Goal:**

- maximum survivability  
- rapid mobility  

**Actions:**

- fully charge all packs as policy allows (still respect BMS) — at base set **[supplement](./pv_routing_swapbox_supplement.md)** auxiliary output priority for swap-pack and confirm auxiliary sizing supports prep timeline  
- install onto boat/vehicle  
- carry modular solar charging capability  
- prioritize direct DC loads  

---

## 14. DC-first philosophy

Strong preference toward:

- native DC operation.  

**Reason:**

- avoid inverter losses.  

**Preferred:**

- USB-C PD  
- direct 24 V appliances  
- DC refrigeration  
- DC lighting  
- DC networking  

---

## 15. Future integration ideas

### Smart energy routing

Potential future additions:

- diversion loads  
- thermal storage  
- smart charging profiles  
- seasonal automation  

**Battery-output automation** after the auxiliary MPPT (SOC-directed routing to BAB vs swap-pack) is summarized in [supplement](./pv_routing_swapbox_supplement.md) §§11–12—not PV string switching automation.

### Thermal integration

Future concepts:

- solar-to-water thermal diversion  
- ballast thermal storage  
- PV cooling loops  
- heat exchanger systems  

---

## 16. Winterization strategy

### Recommended state

| Parameter | Recommendation |
|-----------|----------------|
| SOC | 50–60 % |
| Temperature | Cool |
| Charging | Maintenance / storage SOC only |
| Loads | Disconnected |

### Long-term storage

Potential future feature:

- automated seasonal charging profile  
- maintain storage SOC automatically  

---

## 17. Safety philosophy

Each pack should include:

| Protection | Purpose |
|------------|---------|
| BMS | Electronic protection |
| Fuse | Catastrophic fault protection |
| Disconnect switch | Manual isolation |
| SmartShunt (or equivalent) | Monitoring |
| Proper bus bars | Current distribution |

**Container integrate discipline:** auxiliary MPPT commissioning, isolate-before-service on **each** PV array, and **battery-side** selector sequencing—see [supplement](./pv_routing_swapbox_supplement.md) §§8, 10, 13.

---

## 18. System topology (per pack)

Recommended negative path for a **single** portable pack **on the battery DC side**:

```text
Battery → BMS → SmartShunt → Negative Bus → All Loads/Chargers
```

**Solar at the container:** auxiliary PV feeds the **auxiliary MPPT**, then (**when routed**) the swap-pack—not the studs directly. Selector and conductor classes follow [supplement](./pv_routing_swapbox_supplement.md) §§6–8 (battery-side routing). Insert **charger/source negative** paths per inverter/MPPT manual and applicable code—do not bypass pack BMS rules unless engineer-approved exceptions exist.

---

## 19. Future development areas

### Potential upgrades

- Victron integration  
- Node-RED automation  
- ESPHome monitoring  
- MQTT telemetry  
- smart relay control  
- thermal automation  
- charge profile automation  
- marine integration  
- swappable inverter modules  

Several items overlap the **battery-output automation / telemetry** roadmap in [supplement](./pv_routing_swapbox_supplement.md) §§11–14.

---

## 20. Related documentation

| Document | Role |
|----------|------|
| [Portable / Hot-Swappable 24 V LiFePO₄ Packs (~100 Ah)](./Portable_24v_swap_boxes.md) (this file) | Pack goals, internals, connectors, parallel use, profiles, modes |
| [Supplement — Dual Independent PV Arrays and Battery-Side Auxiliary MPPT Routing](./pv_routing_swapbox_supplement.md) | Two PV arrays + two MPPTs; auxiliary output selector BAB vs swap-box; dual-MPPT-into-BAB rationale; commissioning / safety |

---

## 21. Closing

These ~100 Ah modules remain **portable ESS nodes**. At the container, energy reaches them via the **standalone auxiliary PV + auxiliary MPPT** chain and **battery-side destination selection** documented in **[the supplement](./pv_routing_swapbox_supplement.md)**—not by improvised DC links from BAB nor by multiplexing trackers across shared PV strings.
