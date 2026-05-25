# Supplement — Multi-String PV Routing and Auxiliary MPPT Architecture for Swap-Box Charging

## Purpose

This document supplements the main document:

**[Portable / Hot-Swappable 24 V LiFePO₄ Battery Packs (~100 Ah)](./Portable_24v_swap_boxes.md)**

It specifically defines the architecture for:

- multi-string PV routing,
- auxiliary MPPT charging,
- swap-box charging isolation,
- manual and future automated PV switching,
- and safe solar energy diversion between the primary stationary ESS and portable swap-boxes.

This document intentionally avoids battery-to-battery charging between the stationary bank and the portable packs.

---

# 1. Design Philosophy

The preferred architecture is:

```text
PV → MPPT → Battery
```

rather than:

```text
Battery → DC-DC → Battery
```

The portable swap-boxes are therefore treated as:

- independent battery systems,
- with independent MPPT charging capability,
- powered by selectively diverted PV strings.

This avoids:

- uncontrolled battery-to-battery inrush current,
- forced paralleling of banks with large SOC deltas,
- unnecessary DC-DC conversion losses,
- and sudden battery substitution events at the all-in-one inverter/charger.

---

# 2. Core Architecture

## Stationary System

The primary system remains:

```text
Main PV Array
        │
        ▼
All-in-One Inverter / MPPT
        │
        ▼
BAB (Big Ass Battery)
```

## Portable Swap-Box Charging System

Additional PV strings are routed independently:

```text
Auxiliary PV Pair(s)
        │
        ▼
PV Routing System
        │
        ├──► Main All-in-One MPPT
        │
        └──► Auxiliary MPPT
                  │
                  ▼
           Portable Swap-Box
```

---

# 3. Key Principle

The stationary BAB and the portable swap-boxes do NOT need to be directly electrically connected.

Instead:

- solar energy is dynamically routed,
- each battery system remains independently managed,
- and each MPPT only sees its assigned PV source.

This removes the need for:

- direct battery paralleling,
- convergence charging between banks,
- or DC-DC battery charging.

---

# 4. Multi-String PV Routing

## Example Physical Layout

Example:

- PV Pair 1 → 2 panels in series
- PV Pair 2 → 2 panels in series

Each pair has:

1. a dedicated PV isolator,
2. and an A/OFF/B transfer switch.

---

# 5. Example Routing Topology

```text
PV Pair 1
    │
    ▼
PV Isolator
    │
    ▼
A/OFF/B Transfer Switch
    ├──► A = Main All-in-One MPPT
    └──► B = Auxiliary Swap-Box MPPT


PV Pair 2
    │
    ▼
PV Isolator
    │
    ▼
A/OFF/B Transfer Switch
    ├──► A = Main All-in-One MPPT
    └──► B = Auxiliary Swap-Box MPPT
```

---

# 6. Operational Modes

## Mode A — Full Stationary Charging

```text
Pair 1 → All-in-One
Pair 2 → All-in-One
```

Result:

- 100% PV power available to BAB.

---

## Mode B — Split Charging

```text
Pair 1 → All-in-One
Pair 2 → Swap-Box MPPT
```

Result:

- stationary system charges normally,
- portable swap-box charges independently.

---

## Mode C — Full Swap-Box Charging

```text
Pair 1 → Swap-Box MPPT
Pair 2 → Swap-Box MPPT
```

Result:

- all available diverted PV energy is assigned to portable charging.

This is especially useful when:

- BAB is already full,
- portable packs are depleted,
- or expedition preparation is underway.

---

## Mode D — Maintenance / Isolation

```text
One or more PV pairs → OFF
```

Result:

- complete isolation of selected strings.

Useful for:

- maintenance,
- diagnostics,
- fault isolation,
- or MPPT servicing.

---

# 7. Why This Architecture Is Preferred

## Avoiding MPPT Conflicts

Two MPPT controllers should NOT simultaneously manipulate the same PV source directly.

MPPT controllers continuously:

- adjust operating voltage,
- change current draw,
- track maximum power points.

If two MPPTs attempt to control the same string simultaneously:

- instability may occur,
- efficiency drops,
- and tracking quality suffers.

The routing architecture avoids this entirely by assigning each PV pair to exactly one MPPT at a time.

---

# 8. Switch Requirements

## Transfer Switch Type

Recommended:

```text
A / OFF / B
break-before-make
PV-rated DC transfer switch
```

The switch MUST:

- break the first circuit completely before connecting the second,
- never connect both MPPTs simultaneously,
- and be rated for live PV DC switching.

---

## Electrical Requirements

Switches must be rated above:

| Parameter | Requirement |
|---|---|
| Voc | Cold-weather open-circuit voltage |
| Isc | Short-circuit current with safety margin |
| Voltage class | Entire string voltage |
| DC arc rating | Required |

---

## Pole Count

Preferred:

```text
2-pole switching
```

Meaning:

- PV positive switched,
- PV negative switched.

This simplifies isolation and diagnostics.

---

# 9. Auxiliary MPPT Requirements

The auxiliary swap-box MPPT must support:

| Feature | Requirement |
|---|---|
| LiFePO₄ profiles | Required |
| 24 V battery support | Required |
| Input voltage range | Compatible with routed PV pairs |
| Current handling | Sized for maximum diverted PV |
| Temperature protection | Strongly preferred |
| Adjustable charging | Preferred |

---

# 10. Swap-Box Charging Philosophy

The portable swap-box:

- remains electrically independent,
- maintains its own BMS,
- uses its own MPPT charging path,
- and never requires direct battery-to-battery charging from BAB.

This architecture treats the swap-box as:

```text
portable solar ESS node
```

rather than merely:

```text
portable battery
```

---

# 11. Future Automation

## Phase 1 — Manual Routing

Initially:

- manual PV transfer switches,
- operator-controlled routing.

Advantages:

- simple,
- transparent,
- low-complexity,
- easy diagnostics.

---

## Phase 2 — Automated Routing

Later:

- replace transfer switches with:
  - DC contactors,
  - motorized switches,
  - or relay-controlled transfer systems.

Controller inputs may include:

| Data Source | Purpose |
|---|---|
| BAB SOC | Determine stationary demand |
| Swap-box SOC | Determine portable demand |
| PV availability | Energy routing |
| Battery temperature | Charge safety |
| BMS fault states | Isolation logic |
| Time-of-day | Automation logic |
| Expedition mode | Priority charging |

---

# 12. Example Future Automation Logic

```text
IF swap-box connected AND low SOC:
    divert one PV pair to auxiliary MPPT

IF BAB full:
    divert additional PV to swap-box charging

IF swap-box full:
    restore PV strings to all-in-one

IF fault:
    isolate affected PV pair
```

---

# 13. Important Safety Principles

The routing system MUST:

- remain break-before-make,
- prevent dual-MPPT contention,
- maintain proper PV isolation capability,
- support lockout/tagout servicing,
- and provide clear labeling.

---

# 14. Recommended Development Path

## Stage 1

Build:

- independent PV pair routing,
- manual transfer switching,
- dedicated auxiliary MPPT,
- portable swap-box charging path.

## Stage 2

Add:

- monitoring,
- SOC awareness,
- automation controller,
- relay/contactors,
- telemetry.

## Stage 3

Potential future additions:

- Node-RED integration,
- MQTT telemetry,
- ESPHome monitoring,
- solar prioritization logic,
- expedition charging profiles,
- seasonal automation,
- remote control,
- mobile app integration.

---

# 15. Final Summary

This architecture creates:

- a modular solar routing system,
- independent charging domains,
- flexible PV allocation,
- portable energy autonomy,
- and low-loss charging paths.

The system intentionally avoids:

- direct battery-to-battery charging,
- uncontrolled parallel connection,
- and multi-MPPT contention on shared PV strings.

Instead, energy routing occurs at the PV-string level, allowing:

- full stationary charging,
- full portable charging,
- or dynamic split allocation,
- while keeping both ESS domains electrically independent.
