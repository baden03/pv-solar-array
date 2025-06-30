# Solar Ballast System & Thermal Integration Concepts

This repository documents modular, low-cost, and expandable design ideas for solar panel ballast systems that can double as thermal mass for hot water generation and photovoltaic (PV) panel cooling.

## Overview

The ballast system anchors solar panels on a shipping container roof without drilling, while supporting future thermal integration (hot water, cooling, rainwater reuse). The current recommended build uses 110 mm PVC-U pipes in a zig-zag pattern, but the document also preserves the original 200 mm concept for reference and expansion.

---

## 1. Recommended v1.0: 110 mm PVC-U Ballast System

**Purpose:** Provide sufficient weight to anchor solar panels without drilling, with maximum modularity and cost-effectiveness.

**Current Build Configuration:**
- 6 × 110 mm diameter PVC pipes, 4 m long (main runs)
- 5 × 0.5 m cross-over runs
- 10 × 90º elbows for zig-zag routing
- Total pipe length: 26.5 m
- Total ballast: ~252 L ≈ **~252 kg of water ballast**
- Estimated material cost: **~€290**
- Wall thickness: 2.7 mm PVC-U (sufficient for non-pressurized static water system)

**Advantages:**
- Fewer joints due to 4 m lengths → fewer leak points
- Clean zig-zag routing improves structural rigidity
- Cold-in / hot-out design supports directional thermal flow
- Cross-runs encourage slow, even temperature distribution

**Planned Flow Control:**
- Cold rainwater enters at the lowest point (start of the zig-zag)
- Hot water exits at the highest point (end of the zig-zag), rising into a thermal tank or rain barrel

**Installation Notes:**
- Pipes will be mounted on supports that provide a slight upward rise along the system to encourage thermosiphon flow from the cold inlet to the hot outlet
- UV-stabilized PVC-U will resist degradation, and will be shaded under the PV panels

---

## 2. Pipe Sizing Considerations

**Pros of Smaller Diameter Pipes (e.g., 110 mm):**
- Lower cost and easier handling
- Readily available fittings
- Greater modularity and layout flexibility
- Faster heat-up response for thermal recovery
- Allows more distributed ballast footprint

**Cons:**
- Lower volume per pipe = more pieces and joints
- More fittings = more potential for leaks
- Higher surface area = more thermal loss unless insulated
- Less stiffness compared to 200 mm systems

**Expansion Strategy:**
- Start with a 110 mm system and expand by:
    - Adding additional runs
    - Connecting to larger 200 mm tanks later if needed
    - Integrating with a central rain barrel as thermal buffer and water source

---

## 3. Conceptual Expansion: Combined Thermosiphon + Rainwater Cooling

**Goal:** Keep panels cool, generate hot water, and replace warm ballast with cool water

**Concept:**
- Ballast tanks heat via solar exposure
- Hot water rises via thermosiphon into a thermal tank
- Once hot tank is full or reaches target temp:
    - Rainwater is added to ballast tanks via float valve or diverter
    - Ballast tanks act as heat sinks
    - Cooled ballast increases PV efficiency

**New Addition:**
- A **rain barrel** will be integrated as a **central thermal buffer**, elevated to support thermosiphon flow
- It will serve as both:
  - A **hot water reservoir** for showers
  - A **cold water source** to feed the ballast for solar panel cooling
- Cold rainwater enters ballast low, hot water rises from ballast high into the barrel

---

## 4. Conceptual Foundation: The Original 200 mm Water Ballast Design

*   **Purpose**: Provide sufficient weight to anchor solar panels without drilling into the container roof.
*   **Design Details**:
    *   2 × 200 mm diameter PVC pipes, 4 m long
    *   Connected at one end with 90° elbows and a 0.5 m pipe to form a U-shape.
    *   Mid-point connection with T-connectors and a 0.5 m brace pipe.
    *   Inlet and outlet: garden hose fittings (top fill, bottom drain).
    *   Approximate Volume: 280 L, providing ~280 kg of ballast.
*   **Advantages**:
    *   Inexpensive and readily available materials.
    *   Modular and scalable design.
    *   Stable due to distributed weight and cross-bracing.

---

## 5. Next Steps
- Assemble 6-run 4 m ballast pipe system with zig-zag layout
- Add endpoints with hose valves for drain/fill
- Elevate insulated rain barrel and connect top of ballast to barrel inlet
- Monitor flow behavior, thermal gain, and stability
- Log performance and refine loop design as needed

---

## Thermal Loop Enhancements: Two-Stage Thermosiphon

To improve both heat capture and flow efficiency in passive thermosiphon systems, a secondary heating loop can be added on the upward return path between the ballast and the elevated rain barrel.

### Concept

- The primary ballast pipes are shaded beneath the solar panels and primarily act as thermal mass and panel cooling.
- A **secondary zig-zag run** of pipe is mounted in **direct sunlight** along the upward flow path.
- This sun-exposed section preheats the water before it enters the rain barrel, boosting temperature differential (ΔT) and accelerating natural circulation.

### Benefits

- **Enhanced heat gain** from direct sunlight exposure
- **Stronger thermosiphon effect** due to increased ΔT (hotter outflow vs. cooler inflow)
- **Faster circulation** = more efficient cooling of ballast and improved thermal turnover
- **Higher output temperature** at the top for hot water use
- **Modular addition**: can be mounted on roof, wall, or rail near panels
- **Dual-use**: at night, it can act as a **radiator** to dump excess heat

### Design Notes

- Use 110 mm pipe to match main ballast or optionally reduce to 50–75 mm for faster heating
- Paint booster pipe **black** or use black PVC for maximum solar absorption
- Maintain upward slope from ballast to rain barrel inlet
- Ensure connections are sealed and protected from expansion stress
- Consider adding valves or bypass options if needed for seasonal operation

This two-stage loop is an optional but powerful enhancement that increases both performance and flexibility of your thermal system without requiring active pumps.

---

## Floating Garden & Garden Coil Integration

The floating garden system plays a dual role in the broader water and energy ecology of this project: it serves as a **rainwater filter and biological purifier**, while also acting as a **cool-side thermal exchange** component in the hot water loop.

### System Layout

- The **floating garden tank** is mounted on the roof of the container
- It is **positioned below and shaded by the insulated hot water tank**
- This tank is **open to the air** and contains a **floating garden raft**
- A **coil of pipe or submerged loop** runs through the garden tank and is part of the thermal return system

### Functional Roles

| Function | Description |
|---------|-------------|
| **Rainwater catchment** | Receives and stores pre-filtered rainwater for system use |
| **Biological filtration** | Floating plant roots and bubbler improve water quality |
| **Cooling coil** | A submerged pipe loop bleeds heat from the hot loop return water before it re-enters the ballast |
| **Evaporation buffer** | Shaded tank mitigates excessive thermal gain and maintains relatively cool water |
| **Stabilization** | Helps moderate the temperature of return water, increasing the overall system delta T |

### Thermal Behavior

- Water exiting the insulated rain barrel travels down into the ballast
- Before entering the ballast, it passes through the **cooling coil inside the garden tank**
- This **reduces the temperature** of the input to the ballast system, keeping ballast water cooler
- The cooler ballast supports **more effective PV panel cooling** and a **greater thermosiphon differential**

### Design Notes

- Garden tank should hold 50–100 L minimum to have thermal mass and biological inertia
- Coil can be 32–50 mm black flexible tubing or rigid PVC
- Coil should be **submerged and secured** beneath the floating raft
- Optional bubbler or passive aeration helps maintain water clarity and plant health
- Overflow from garden tank can route to ground or to additional use (e.g., greywater bed)

This system not only improves water quality and reuse, but enhances overall thermal performance by passively pre-cooling the return side of the loop — enabling better energy separation and stronger heat capture.

---

## Performance Expectations: Estimated Temperatures & Thermal Delta

This section provides realistic estimates for temperature ranges across various parts of the closed-loop hot water ballast system, based on passive solar heating, thermosiphon flow, and the addition of a garden coil as a cool-side thermal bleed.

### Estimated Temperature Ranges (Summer, Full Sun)

| System Component                | Estimated Temp Range | Notes |
|--------------------------------|-----------------------|-------|
| Solar Booster Pipe (sun-exposed) | 45–65 °C             | Black pipe in direct sunlight |
| Ballast Pipes (shaded under PV)  | 35–45 °C             | Absorbs ambient + indirect heat from panels |
| Outlet to Hot Tank               | 40–60 °C             | Depends on flow speed and booster efficiency |
| Insulated Hot Water Barrel (top layer) | 50–65 °C       | Stratified if drawdown is moderate |
| Garden Coil (shaded, partially buried) | 20–30 °C       | Passive cooling loop, aids thermal delta |
| Ballast Inlet (post-garden coil) | 25–35 °C            | Pre-chilled return improves circulation |

### On Cooler or Overcast Days

| System Component | Estimated Temp Range |
|------------------|-----------------------|
| Booster Pipe     | 30–45 °C              |
| Ballast System   | 25–35 °C              |
| Hot Tank (top)   | 35–45 °C              |
| Garden Coil      | 15–25 °C              |
| Ballast Inlet    | 20–30 °C              |

### Thermal Delta (ΔT) Between System Points

| Between                        | Estimated ΔT | Result |
|-------------------------------|---------------|--------|
| Ballast outlet → Booster pipe → Hot tank | +10–20 °C | Enhances flow and top-end temperature |
| Hot tank bottom → Garden coil → Ballast inlet | –10–20 °C | Cools return water, increasing ΔT |
| Top vs Bottom of Hot Tank     | Up to 30 °C    | Enables hot water draw without full mixing |

### Key Factors That Influence Performance

- Surface area and solar exposure of booster loop
- Quality of insulation on the hot tank
- Shading and thermal inertia of garden coil tank
- Height differences to support thermosiphon flow
- Nighttime cooling (radiative and ambient)

### Monitoring Recommendations

- Install temperature probes at key locations:
  - Booster pipe
  - Ballast inlet/outlet
  - Top & bottom of insulated rain barrel
  - Garden coil output
- Use Arduino or ESP32 for temperature logging if needed

These numbers provide a baseline to understand and optimize your system’s behavior, helping you improve flow, conserve thermal energy, and adapt your usage strategy seasonally.

