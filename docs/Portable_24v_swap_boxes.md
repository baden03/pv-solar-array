# Portable / Hot-Swappable 24 V LiFePO₄ Battery Packs (~100 Ah)

## Overview

This document describes **modular ~100 Ah, 24 V LiFePO₄ packs** meant to be hot-swapped, carried, and redeployed (base, vehicle, boat, expedition). It covers design goals, internal architecture, connectors, parallel use, charging philosophy, balancing concepts, safety, and operating modes.

**How swap-boxes charge from the container’s solar** (multi-string routing, auxiliary MPPT, transfer switching, and why domains stay independent) is specified in the companion:

**→ [Supplement — Multi-String PV Routing and Auxiliary MPPT for Swap-Box Charging](./pv_routing_swapbox_supplement.md)**

That supplement adopts **`PV → MPPT → Battery`** for the portable domain and **does not** use direct **battery-to-battery** charging from the stationary bank into the swap-boxes. This document stays on **pack-level** behavior; string-level wiring, switch ratings, and ESS isolation live in the supplement.

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
| Daily use | Site-supported use: one pack on loads while another charges via **routed PV → auxiliary MPPT** at base (see supplement), or via shore / vehicle / other approved charger |
| Weekend mode | Single-pack portable power away from base |
| Travel mode | 1–3 week excursions |
| Expedition mode | Multi-month off-grid with rotation / redundancy |
| Winterization mode | Long-term storage of all packs |
| Emergency / Bug-out mode | Rapid evacuation / marine deployment |

Modules stay **energy units** you move between contexts—not a single permanent install.

Independence from any one tether:

- not locked to one building or vessel layout  
- at the container, **solar** coupling is by **PV diversion** to a **dedicated MPPT**, not by paralleling pack and stationary bank (see [supplement](./pv_routing_swapbox_supplement.md))  

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

### Charging at base — auxiliary MPPT and PV routing (preferred)

When moored at the container install, the **intended** charge path for swap-boxes is:

```text
Auxiliary routed PV strings → Auxiliary MPPT → Portable swap-box
```

in parallel conceptually with the stationary path:

```text
Main PV (other strings/pairs) → All-in-One MPPT → Stationary ESS
```

String-level **isolators**, **break-before-make A/OFF/B** transfer switches, **operating modes** (full BAB / split / full portable / maintenance OFF), avoidance of dual-MPPT contention, and equipment requirements are all defined in **[Supplement — Multi-String PV Routing and Auxiliary MPPT for Swap-Box Charging](./pv_routing_swapbox_supplement.md)**.

**Important:** Direct **stationary bank → portable pack** DC charging is **not** part of the architecture; routing energy at the **PV** layer keeps banks independent and avoids large SOC-delta mismatch issues.

### Other charging sources

When away from base or as a supplement:

- shore **AC → DC** LiFePO₄-aware charger  
- vehicle or boat DC (only where voltage, current, and BMS rules allow)  
- portable solar arrays with their **own** MPPT/charger—not shared with container strings unless integrated via the routing rules in the supplement  

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

At the container, **PV** lands on the **auxiliary MPPT** input after routing (per [supplement](./pv_routing_swapbox_supplement.md)), not on the pack studs directly.

---

## 7. Connector standardization

### Anderson connectors

Preferred ecosystem standard for **pack DC** (loads, parallel mates, chargers that connect at the battery DC bus). PV string combiners / transfer gear use **PV-rated** gear per the routing supplement—not necessarily Anderson on the DC string side.

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
- second pack charging from **diverted PV → auxiliary MPPT** (manual transfer switches first; future automation per [supplement](./pv_routing_swapbox_supplement.md) §11–12)  
- or charging from shore / AC charger when solar routing is not in use  

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

This addresses **pack-to-pack** paralleling for load sharing. It does **not** replace the supplement rule: avoid **stationary ESS ↔ portable pack** DC tie for charging—use **PV routing** instead.

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

**Container / shared array:** Align operation with **[supplement](./pv_routing_swapbox_supplement.md)**—assign each PV pair to **one** MPPT at a time (break-before-make routing) so trackers do not fight the same string.

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

Targets for **24 V nominal** packs when configuring **battery-side** charging (auxiliary MPPT, shore charger, or other DC source meeting BMS limits). **PV-side** voltage/current are set by the auxiliary MPPT and the routed string Voc/Isc—see [supplement](./pv_routing_swapbox_supplement.md) §§5–9.

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
- Charge a second pack at base via **routed PV → auxiliary MPPT** (per [supplement](./pv_routing_swapbox_supplement.md)), or via approved non-solar chargers when needed  

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

- fully charge all packs (if policy allows; still respect BMS) — at base, prefer **full swap-box charging** PV mode from the [supplement](./pv_routing_swapbox_supplement.md) when preparing  
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

**PV routing automation** (SOC-driven string diversion, contactors vs manual switches) is sketched in [supplement](./pv_routing_swapbox_supplement.md) §§11–12 and can share telemetry with items below.

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

**PV routing** adds requirements: break-before-make transfer switching, Voc/Isc-rated gear, labeling, LOTO—see [supplement](./pv_routing_swapbox_supplement.md) §§8 and 13.

---

## 18. System topology (per pack)

Recommended negative path for a **single** portable pack **on the battery DC side**:

```text
Battery → BMS → SmartShunt → Negative Bus → All Loads/Chargers
```

**Solar at the container:** PV energy reaches the pack only after **auxiliary MPPT** regulation (preceded by isolators and transfer switches as in the [supplement](./pv_routing_swapbox_supplement.md)). Do not connect raw PV strings directly to the battery studs. When charging from base, insert the **charger/source negative** according to manufacturer and code at the engineered negative bus junction—do not bypass BMS monitoring unless explicitly allowed.

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

Several items overlap the **automated PV routing** roadmap in [supplement](./pv_routing_swapbox_supplement.md) §§11–14.

---

## 20. Related documentation

| Document | Role |
|----------|------|
| [Portable / Hot-Swappable 24 V LiFePO₄ Packs (~100 Ah)](./Portable_24v_swap_boxes.md) (this file) | Pack goals, internals, connectors, parallel use, profiles, modes |
| [Supplement — Multi-String PV Routing and Auxiliary MPPT for Swap-Box Charging](./pv_routing_swapbox_supplement.md) | PV isolators, A/OFF/B routing, aux MPPT, modes, switch ratings, no B2B charging |

---

## 21. Closing

These ~100 Ah modules are **portable solar-capable ESS nodes**: electrically **independent** from the stationary bank, with **container-side charging** delivered by **diverted PV → dedicated MPPT** as specified in the **[routing supplement](./pv_routing_swapbox_supplement.md)**—not by dc-lashing two battery systems together.
