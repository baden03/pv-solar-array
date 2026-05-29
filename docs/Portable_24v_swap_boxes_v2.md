# Portable / Hot-Swappable 24 V LiFePO₄ Battery Packs (~100 Ah)

## Overview

This document describes **modular ~100 Ah, 24 V LiFePO₄ packs** meant to be hot-swapped, carried, and redeployed (base, vehicle, boat, expedition). It covers design goals, internal architecture, connectors, parallel use, charging philosophy, balancing concepts, safety, and operating modes.

**How swap-boxes charge from the container's solar** (dedicated auxiliary PV array, auxiliary MPPT, **battery-side** destination routing, dual-array independence) is specified in the companion:

**→ [Supplement — Dual Independent PV Arrays and Battery-Side Auxiliary MPPT Routing](./pv_routing_swapbox_supplement.md)**

That supplement uses **`Aux PV → Auxiliary MPPT → BAB or Swap-Box`** (selector after the auxiliary MPPT) and **`Main PV → AIO MPPT → BAB`** with **no** PV string transfer or MPPT sharing. Direct **battery-to-battery** charging from BAB into a swap-pack is **not** the plan—charge enters packs via **MPPT** or approved chargers. This file stays **pack-level**; array layout, auxiliary MPPT coordination, switching sequences, and dual-charger etiquette on BAB live in the supplement.

**Three container-side charging architectures** are described in this ecosystem:

| Option | Summary | Status |
|--------|---------|--------|
| [Option A — DC-DC Charger (Victron Orion XS)](./option_a_dcdc_charger.md) | BAB → Orion XS 1400 → Swap-Box; simplest path to working system | Recommended first step |
| [Option B — Dedicated Auxiliary PV Array](./pv_routing_swapbox_supplement.md) | Separate 2-panel array → Auxiliary MPPT → A/OFF/B → BAB or Swap-Box | Expandable, no conversion loss |
| [Option C — Battery Gatekeeper](./option_c_battery_gatekeeper.md) | Intelligent SOC-aware routing and soft-parallel unit between charger and two banks | Concept / future development |

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

### Swappable 100 Ah modules (design focus)

- 24 V nominal LiFePO₄  
- ~100 Ah per pack (~2.5 kWh)  

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
- portable PV with its **own** MPPT—not by tapping the container's auxiliary or main PV homeruns without a full redesign  
---

## 3. Design goals

### Required features — electrical

- 24 V native  
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

## 4. Why 24 V?

24 V was selected because:

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
- 24 V nominal  
- ~100 Ah  

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
| Optional DC outputs | Direct 24 V appliances |

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
| Voltage delta < 0.1 V | Generally safe |
| Similar chemistry | Required |
| Similar cell count | Required |
| Similar nominal voltage | Required |

---

## 10. Charging philosophy

### Normal use

Do **not** hold at 100 % SOC continuously when avoidable.

Instead:

- cycle on real loads or solar,  
- periodically reach top balance per BMS / service needs.  

**Two independent container arrays:** there is **no** PV-string transfer—the main and auxiliary trackers each serve **their own** array. Follow **[supplement](./pv_routing_swapbox_supplement.md)** for isolators, commissioning order, auxiliary output destination, and auxiliary↔BAB coexistence assumptions.

### Long-term storage

Target:

- ~50–60 % SOC  
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

Targets for **24 V nominal** packs when configuring **battery-side** regulation (auxiliary MPPT targeting swap-pack, shore charger, or equivalent). **Auxiliary Voc/Isc sizing** sits at **that array ↔ auxiliary MPPT** interface—see [supplement](./pv_routing_swapbox_supplement.md) §§9–10.

### Operational profile

| Setting | Typical target |
|---------|----------------|
| Bulk / absorption | ~27.8 V |
| Float | ~27.0 V or disabled |
| Daily SOC | 20–90 % preferred |

### Storage profile

| Setting | Target |
|---------|--------|
| SOC | 50–60 % |
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

## 13. Operational modes (100 Ah packs)

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
- reduced SOC (~50–60 %)  
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
- direct 24 V appliances  
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
| SOC | 50–60 % |
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

## 20. Option C — Battery Gatekeeper (concept)

### Overview

The Battery Gatekeeper is a proposed intelligent device that sits between a charge source (MPPT or all-in-one inverter/charger) and two battery banks — in this case, the BAB and a swap-box. Rather than using a manual selector switch or a simple DC-DC charger, the gatekeeper autonomously routes charge energy to whichever bank needs it most, and manages the transition to parallel operation once both banks reach parity.

This device does not exist as an off-the-shelf product. It would need to be designed and built, either as a custom unit or assembled from discrete components with a microcontroller managing the logic.

---

### Core function

```text
Charge source (MPPT / AIO) → Battery Gatekeeper → Bank A (BAB)
                                                 → Bank B (Swap-Box)
```

The gatekeeper:

1. Detects when a second bank is connected (e.g. hungry swap-box plugged in)  
2. Routes charge preferentially to the more depleted bank  
3. Monitors both banks continuously  
4. Soft-connects the banks in parallel once SOC parity is reached  
5. Steps aside and allows the charge source to treat both banks as one  
6. Responds to BMS disconnect events from either bank without disturbing the other  

---

### Sub-system 1 — SOC estimation

The flat discharge curve of LiFePO₄ makes voltage-only SOC estimation unreliable in the mid-range (roughly 20–80% SOC). The difference in resting voltage between 30% and 60% SOC is only ~50–100 mV on a 24 V pack — well within measurement noise and cell-to-cell variation.

**Recommended approach: hybrid coulomb counting + voltage calibration**

| Method | How it works | Limitation |
|--------|-------------|------------|
| Voltage-only | Read terminal voltage, map to SOC curve | Unreliable 20–80% SOC on LiFePO₄ |
| Coulomb counting | Integrate current in/out over time | Drifts; needs periodic reset |
| Hybrid | Use coulomb counting in mid-range; use voltage at knee points (< ~20% or > ~90% SOC) to calibrate and reset the counter | Best accuracy; standard approach in quality BMS designs |

The gatekeeper's microcontroller tracks net amp-hours in and out of each bank from a known reference point (typically last full charge). Voltage is used at the extremes to detect full-charge and near-empty states, which resets the coulomb counter and prevents long-term drift.

**Practical implication:** When a swap-box is first plugged in after a partial discharge, the gatekeeper may have imprecise knowledge of its exact SOC if it has never seen a full-charge event on that pack. In this case, a conservative strategy is to assume the pack is more depleted than voltage alone suggests, and charge it first until a voltage knee or BMS signal confirms the pack is approaching full.

---

### Sub-system 2 — Charge routing logic

#### State machine (simplified)

| State | Condition | Action |
|-------|-----------|--------|
| Single bank | Only BAB connected | Pass-through; normal operation |
| Second bank detected | Swap-box plugged in; large SOC delta | Isolate BAB from charger output; charge swap-box exclusively |
| Balancing | Swap-box SOC rising toward BAB | Continue routing to swap-box |
| Parity approaching | SOC delta < configurable threshold (e.g. 5–10%) | Begin soft-connect sequence |
| Parallel | Both banks at parity | Open gate; both banks see charger as one |
| BMS trip (either bank) | BMS disconnects one bank | Immediately isolate that bank; continue on surviving bank |

#### Parity threshold

"Close enough to parallel" is not a fixed voltage number on LiFePO₄. Given the flat curve, a practical approach is:

- Use SOC estimate (from coulomb counter) rather than raw voltage as the parity metric  
- Set a configurable threshold (e.g. ± 5 Ah or ± 5% SOC) as the trigger for soft-connect  
- Perform a brief pre-connect voltage check as a final sanity gate before closing the parallel contactor  

---

### Sub-system 3 — The physical gate

The "gate" is the switching element that connects or isolates the two banks. Options:

| Switch type | Pros | Cons |
|-------------|------|------|
| Relay / contactor | Simple, cheap, proven | Hard switching; arcing risk at high current; no soft-start |
| MOSFET array (bidirectional) | Soft switching; no arcing; fast response | Higher cost; heat management; complexity |
| DC-DC converter (bidirectional) | Full current control; can charge one bank from the other | Most complex; highest cost; conversion losses |
| Pre-charge resistor + contactor | Simple soft-start before hard parallel | Only solves inrush, not ongoing routing |

**Recommended approach for V1:** a **pre-charge resistor circuit** followed by a **contactor**, controlled by the microcontroller. This avoids the arcing and inrush problem without the full complexity of a MOSFET array. A bidirectional DC-DC would be the ideal long-term solution for maximum flexibility.

---

### Sub-system 4 — BMS coordination

Each battery has its own BMS which can disconnect its bank under fault conditions (over-voltage, under-voltage, over-temperature, over-current). The gatekeeper must:

- monitor each bank's BMS output (typically a relay signal or voltage presence on the pack terminal)  
- immediately isolate a faulted bank without disturbing the other  
- log the fault event  
- not attempt to reconnect a faulted bank automatically — require manual reset  

**Key design constraint:** the gatekeeper must never allow a BMS trip on one bank to cascade into a fault on the other. Isolation must be fast (< 100 ms) and unconditional.

---

### Hardware sketch (V1 concept)

```text
Charge source (+) ──── Gatekeeper input ──┬── [Contactor A] ── BAB (+)
                                           └── [Contactor B + pre-charge] ── Swap-Box (+)

Charge source (−) ──── Common negative bus ─── BAB (−) / Swap-Box (−)

Microcontroller:
  - Reads: shunt current (Bank A), shunt current (Bank B)
  - Reads: terminal voltage (Bank A), terminal voltage (Bank B)
  - Reads: BMS status signal (Bank A), BMS status signal (Bank B)
  - Reads: plug-detect (Bank B Anderson connector presence)
  - Controls: Contactor A, Contactor B, pre-charge relay
  - Outputs: status LED / display, MQTT telemetry (optional)
```

---

### Open design questions

| Question | Notes |
|----------|-------|
| What is the maximum charge current the gatekeeper must handle? | Sized by charge source — up to ~60 A at 24 V for a 1400 W MPPT |
| How is coulomb counter reset on a pack that was charged externally? | Manual reset button, or BMS full-charge signal if available |
| What happens if swap-box BMS does not expose a status signal? | Fall back to terminal voltage monitoring; less reliable |
| Should the gatekeeper support more than 2 banks? | Future extension — adds complexity to routing logic |
| Enclosure and thermal management | Contactor and wiring will generate heat at high charge currents |
| Communication | Victron VE.Bus / MQTT / BLE for monitoring integration |

---

### Relationship to Options A and B

Option A (Orion XS DC-DC) solves the inrush problem only — it does not provide SOC-aware routing or automatic parallel connection. It is the recommended first step due to simplicity and immediate availability.

Option B (dedicated auxiliary PV array) provides independent charge paths but requires manual A/OFF/B switching to direct energy.

Option C (gatekeeper) would replace or complement Options A and B by automating the routing and parallel management logic, with no manual switching required once a swap-box is plugged in. It is best understood as the "smart layer" that could sit on top of either of the other architectures.

---

## 21. Related documentation

| Document | Role |
|----------|------|
| [Portable / Hot-Swappable 24 V LiFePO₄ Packs (~100 Ah)](./Portable_24v_swap_boxes.md) (this file) | Pack goals, internals, connectors, parallel use, profiles, modes |
| [Supplement — Dual Independent PV Arrays and Battery-Side Auxiliary MPPT Routing](./pv_routing_swapbox_supplement.md) | Two PV arrays + two MPPTs; auxiliary output selector BAB vs swap-box; dual-MPPT-into-BAB rationale; commissioning / safety |
| [Option A — DC-DC Charger (Victron Orion XS)](./option_a_dcdc_charger.md) | BAB → Orion XS 1400 → Swap-Box; simplest container-side charging path |
| [Option C — Battery Gatekeeper](./option_c_battery_gatekeeper.md) | SOC-aware intelligent routing and soft-parallel unit; concept and design specification |

---

## 22. Closing

These ~100 Ah modules remain **portable ESS nodes**. At the container, energy reaches them via the **standalone auxiliary PV + auxiliary MPPT** chain and **battery-side destination selection** documented in **[the supplement](./pv_routing_swapbox_supplement.md)**—not by improvised DC links from BAB nor by multiplexing trackers across shared PV strings.

Three container-side charging architectures have been defined: **Option A** (Victron Orion XS DC-DC, recommended starting point), **Option B** (dedicated auxiliary PV array, more expandable), and **Option C** (Battery Gatekeeper, intelligent SOC-aware routing, future development). These options are complementary and can evolve in parallel.
